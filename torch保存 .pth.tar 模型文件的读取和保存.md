torch保存的模型有很多形式，前几天下载别人预训练好的模型后发现是 .pth.tar 后缀的文件，开始以为是压缩文件，使用tar -xvf 命令解压，结果报错。后经过搜索资料，发现不需要解压，直接使用 torch.load 直接加载模型就可以了
- 查看 .pth.tar 文件模型参数
```
import torch
import torchvision.models as models

checkpoint = torch.load('resnet50_train_60_epochs-c8e5653e.pth.tar')	# 加载模型
print(checkpoint.keys())												# 查看模型元素
state_dict = checkpoint['state_dict']

print(checkpoint['epoch'])
print(checkpoint['arch'])
print(checkpoint['best_prec1'])
# print(checkpoint['ce_optimizer'])
print(state_dict.keys())
print(state_dict['module.bn1.bias'])									# 打印 module.bn1.bias 的权值
print(state_dict['module.bn1.bias'])									# 打印 module.bn1.bias 的形状
```
- 由 .pth.tar 文件加载模型
```
import torch
import torchvision.models as models

checkpoint = torch.load('resnet50_train_60_epochs-c8e5653e.pth.tar')
arch = checkpoint['arch']
model = models.__dict__[arch]()
model = torch.nn.DataParallel(model).cuda()
model.load_state_dict(checkpoint['state_dict'])
# print(model.state_dict())
# print(model)
```
- 保存模型（只保存参数）
```
torch.save(model.state_dict(), 'resnet50_only_paramater.pth')   #只保存模型权重参数，不保存模型结构
```
- 保存模型（保存全部）
```
torch.save(model, 'resnet50_all.pth')      #保存整个模型，包括模型权重和模型结构
```

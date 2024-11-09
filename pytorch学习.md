# Pytorch学习

## 1.python学习中的两大法宝函数

### 1.1 dir();

作用：打开，看见

能让我们知道 工具箱以及工具箱中的分隔区有什么东西

### 1.2 help();

作用：说明书

能让我们知道每个工具是如何使用的，工具的使用方法

注：help里面是函数

## 2.pytorch加载数据初认识

![image-20240730220955601](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240730220955601.png)

### 2.1 读取数据

#### 1.Dataset

提供一种方式去获取数据及其label

#### 2.Dataloader

为后面的网络提供不同的数据形式

#### 3.代码实现

##### 3.1 read_data

读取数据集中的数据

```python
from torch.utils.data import Dataset
from PIL import Image
import os
class MyDataset(Dataset):
    def __init__(self,root_dir,label_dir):
        self.root_dir = root_dir
        self.label_dir = label_dir
        self.path = os.path.join(self.root_dir,self.label_dir)
        self.img_path =  os.listdir(self.path)
    def __getitem__(self, index):
        img_name = self.img_path[index]
        img_path = os.path.join(self.root_dir,self.label_dir,img_name)
        image = Image.open(img_path)
        label = self.label_dir
        return image,label
    def __len__(self):
        return len(self.img_path)
root_dir = "C:\\pythonProject3\\pytorch\\hymenoptera_data\\train"
ants_label_dir = "ants"
bees_label_dir = "bees"
ants_dataset = MyDataset(root_dir,ants_label_dir)
bees_dataset = MyDataset(root_dir,bees_label_dir)
train_dataset = ants_dataset + bees_dataset
len(train_dataset)
```

##### 3.2 rename_data

在处理一个图像数据集时，为每个图像文件在其对应的标签目录下创建一个包含标签信息的文本文件。

```python
import os
root_dir = "C:\\pythonProject3\\pytorch\\hymenoptera_data\\train"
target_dir = "ants_image"
img_path = os.listdir(os.path.join(root_dir, target_dir))
label = target_dir.split('_')[0]
out_dir = "ants_label"
for i in img_path:
    file_name = i.split('.jpg')[0]
    with open(os.path.join(root_dir, out_dir,"{}.txt".format(file_name)), 'w') as f:
        f.write(label)
```

##### 3.3 `self.path = os.path.join(self.root_dir,self.label_dir)`

- `os.path.join(path1[, path2[, ...]])` 是 Python 的 `os.path` 模块中的一个函数，用于将多个路径组件合并成一个路径。这个函数会智能地处理不同操作系统中的路径分隔符问题（比如 Windows 使用反斜杠 `\`，而 UNIX/Linux/macOS 使用正斜杠 `/`）。
- 在这行代码中，`self.root_dir` 是图像数据的根目录路径，而 `self.label_dir` 是特定类别的子目录名称。通过将这两个路径组件合并，我们得到了包含该类别图像文件的完整目录路径，并将这个路径赋值给 `self.path`。
- 例如，如果 `self.root_dir` 是 `"C:\\pythonProject3\\pytorch\\hymenoptera_data\\train"`，且 `self.label_dir` 是 `"ants"`，那么 `self.path` 将被设置为 `"C:\\pythonProject3\\pytorch\\hymenoptera_data\\train\\ants"`。

##### 3.4 `self.img_path = os.listdir(self.path)`

- `os.listdir(path)` 是 Python 的 `os` 模块中的一个函数，用于列出指定路径下的所有文件和目录名，并返回一个列表。
- 在这行代码中，`self.path` 是上一步计算得到的包含特定类别图像文件的目录路径。通过调用 `os.listdir(self.path)`，我们获取了该目录下所有文件和目录的名称列表，并将这个列表赋值给 `self.img_path`。
- 需要注意的是，`self.img_path` 现在包含的是文件名和目录名的混合列表，但在大多数情况下，我们希望它只包含图像文件的名称。如果目录中还包含非图像文件或子目录，并且我们想要过滤掉它们，我们可能需要在将列表赋值给 `self.img_path` 之前对其进行额外的处理（例如，使用列表推导式和文件扩展名检查来过滤文件）。
- 然而，在许多实际应用中，如果数据集组织得当（即 `self.path` 目录下只包含图像文件），那么这行代码就足够了。

##### 3.5 `def __getitem__(self, index):`

在Python中，`def __getitem__(self, index):` 是类的一个特殊方法（也称为魔术方法或双下方法），它允许类的实例支持通过索引（如使用方括号 `[]`）来访问其元素。这个方法通常在自定义的容器类（如列表、元组、字典等的自定义版本）或数据集类中实现，以便能够按照索引或键来检索元素。

在你给出的上下文中，`MyDataset` 类继承自 PyTorch 的 `Dataset` 类，用于加载和预处理图像数据。`__getitem__` 方法在这个类中的实现非常重要，因为它定义了如何根据给定的索引（`index`）来检索和返回单个数据样本（在这里是图像和对应的标签）。

具体来说，`__getitem__` 方法的实现通常包含以下步骤：

1. **根据索引检索数据**：使用索引 `index` 来从内部存储的数据中检索出对应的数据样本。在 `MyDataset` 类中，这通常意味着从 `self.img_path`（一个包含图像文件名的列表）中检索出第 `index` 个文件名。
2. **加载和预处理数据**：使用检索到的文件名（或其他标识符）来加载相应的数据（如图像），并进行必要的预处理（如调整大小、裁剪、归一化等）。在 `MyDataset` 类中，这通常通过打开图像文件（使用PIL的`Image.open`）来完成，并且可能还包含一些图像处理的步骤。
3. **返回数据样本**：将加载并预处理后的数据样本（以及可能的标签或其他元数据）返回。在 `MyDataset` 类中，这通常是一个包含图像和标签的元组或字典。

##### 3.6 `img = Image.open(img_path)`

`img = Image.open(img_path)` 这行代码是使用Python的Pillow库（PIL的一个友好分支）来打开并加载一个图像文件的示例。这里的 `Image` 是Pillow库中用于图像处理的一个模块，而 `open` 是该模块中的一个函数，用于打开一个图像文件。

具体来说：

- `Image`：这是Pillow库中用于图像处理的模块，它提供了大量的图像操作功能，如打开、保存、显示图像，以及进行各种图像变换等。
- `open(img_path)`：这是 `Image` 模块中的 `open` 函数，它接受一个字符串参数 `img_path`，该参数指定了要打开的图像文件的路径。函数会尝试打开该路径下的图像文件，并返回一个 `Image` 对象，该对象包含了图像的数据和一系列可以用于图像处理的方法。
- `img = ...`：这里将 `open` 函数返回的 `Image` 对象赋值给变量 `img`。之后，你就可以通过 `img` 变量来访问和操作这个图像了。

因此，`img = Image.open(img_path)` 这行代码的作用是：打开位于 `img_path` 路径下的图像文件，并将该图像加载为一个 `Image` 对象，然后将这个对象赋值给变量 `img`。

##### 3.7 `label = target_dir.split('_')[0]`

`label = target_dir.split('_')[0]` 这行代码的作用是从变量 `target_dir` 的字符串值中分割出第一个由下划线 `_` 分隔的部分，并将这个部分赋值给变量 `label`。

具体来说：

- `target_dir` 是一个字符串变量，假设它包含了一个或多个由下划线 `_` 分隔的单词或字符串片段。例如，如果 `target_dir = "ants_image"`，那么它就包含了两个由下划线分隔的部分：`"ants"` 和 `"image"`。
- `.split('_')` 是一个字符串方法，它接受一个分隔符作为参数（在这个例子中是下划线 `_`），并返回一个列表，列表中包含了原字符串被该分隔符分割后的所有部分。继续上面的例子，`"ants_image".split('_')` 会返回 `["ants", "image"]`。
- `[0]` 是对 `.split('_')` 方法返回的列表进行索引访问的操作，用于获取列表中的第一个元素。在上面的例子中，`["ants", "image"][0]` 会返回 `"ants"`。

因此，`label = target_dir.split('_')[0]` 这行代码的作用就是从 `target_dir` 字符串中提取出第一个由下划线分隔的部分，并将其作为标签名存储在变量 `label` 中。这种命名约定通常用于数据集组织，其中目录名或文件名包含了关于数据内容的有用信息（如类别标签）。在这个例子中，假设 `target_dir` 表示的是包含特定类别图像的子目录，那么通过分割目录名并取第一部分，就可以轻松地提取出该类别的图像所对应的标签。

## 3.TensorBoard的使用

​	![image-20240731164925178](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240731164925178.png)

### 1.tensorboard --logdir=事件文件所在文件名

**tensorboard --logdir=logs** 是一个命令行指令，‌用于指定 TensorBoard 读取日志文件的目录。‌

### 2.改变端口名

tensorboard --logdir=logs --port=6007

### 3.tensorboard的使用--画一个y=x的图像

```python
from torch.utils.tensorboard import SummaryWriter
writer = SummaryWriter('logs')
# writer.add_image()
# y = x
for i in range(100):
    writer.add_scalar('y = 2x', 3*i, i)
writer.close()
```

### 4.tensorboard的使用--图片的读取

```python
from torch.utils.tensorboard import SummaryWriter
import numpy as np
from PIL import Image
writer = SummaryWriter('logs')
image_path = "C:\\pythonProject3\\pytorch\\data\\train\\ants_image\\5650366_e22b7e1065.jpg"
img_PIL = Image.open(image_path)
img_arrray = np.array(img_PIL)
writer.add_image("test", img_arrray,2,dataformats='HWC')
# y = x
for i in range(100):
    writer.add_scalar('y = 2x', 3*i, i)
writer.close()
```

**加载并处理图像**

```py
image_path = r"C:\pythonProject3\pytorch\data\train\ants_image\5650366_e22b7e1065.jpg"  
img_PIL = Image.open(image_path)  
img_array = np.array(img_PIL)
```

- `image_path` 是一个字符串，指向要加载的图像文件的路径。注意这里使用了原始字符串（在字符串前加 `r`），以避免在 Windows 路径中的反斜杠 `\` 被解释为转义字符。
- `Image.open(image_path)` 使用 Pillow 库打开图像文件，并返回一个图像对象 `img_PIL`。
- `np.array(img_PIL)` 将图像对象转换为 NumPy 数组 `img_array`，以便进行进一步的处理或将其写入 TensorBoard。

**向 TensorBoard 添加图像**

```py
writer.add_image("test", img_array, 2, dataformats='HWC')
```

- `writer.add_image` 方法用于将图像数据写入 TensorBoard。
- 第一个参数 `"test"` 是图像的标签或名称，用于在 TensorBoard 的界面中标识这个图像。
- 第二个参数 `img_array` 是包含图像数据的 NumPy 数组。
- 第三个参数 `2` 是全局步数（global step），用于在 TensorBoard 中按时间顺序组织数据。在这个例子中，它被设置为 2，但通常你会根据迭代次数或其他时间相关的度量来设置这个值。
- `dataformats='HWC'` 指定图像数据的格式是高度（Height）、宽度（Width）、通道（Channels）。这是从 PIL 加载图像时常见的格式。

**向 TensorBoard 添加标量**

```py
for i in range(100):  
    writer.add_scalar('y = 2x', 2*i, i)
```

- 这个循环使用 `writer.add_scalar` 方法向 TensorBoard 写入 100 个标量点。
- 第一个参数 `'y = 2x'` 是标量的标签或名称，用于在 TensorBoard 的界面中标识这个序列。
- 第二个参数 `2*i` 是标量的值，这里模拟了一个 `y = 2x` 的关系（尽管变量名 `i` 通常代表 `x` 的值）。
- 第三个参数 `i` 是全局步数，与图像添加的第三个参数相同，用于在 TensorBoard 中按时间顺序组织数据。

### 5.SummaryWriter()

SummaryWriter 创建一个tensorboard文件, 文件保存在log_dir 目录(自己指定的目录)写文件，该文件可以被tensorboard解析

参数：
log_dir: 保存目录位置。 默认值为 run/CURRENT_DATETIME_HOSTNAME ，每次运行后都会更改。
使用分层文件夹结构可以轻松比较运行情况。 例如 为每个新实验传递“ runs / exp1”，“ runs / exp2”等，以便在它们之间进行比较。
flush_secs: 表示写入tensorboard文件的时间间隔

调整方式：

```py
writer = SummaryWriter(log_dir='logs',flush_secs=60)
```

### 6.writer.add_graph()

这个函数用于在tensorboard中创建Graphs，Graphs中存放了网络结构，其中常用参数有：

model：pytorch模型
input_to_model：pytorch模型的输入

### 7.writer.add_scalar()

这个函数用于在tensorboard中加入loss，其中常用参数有：

tag：标签，如下图所示的Train_loss
scalar_value：标签的值
global_step：标签的x轴坐标

```py
writer.add_scalar('Train_loss', loss, (epoch*epoch_size + iteration))
```

### 8.writer.add_image()

`writer.add_image` 是 PyTorch 中 `torch.utils.tensorboard.SummaryWriter` 类的一个方法，它用于在 TensorBoard 的可视化界面中添加图像。TensorBoard 是 TensorFlow 的一个可视化工具，但 PyTorch 通过 `torch.utils.tensorboard` 模块也提供了对 TensorBoard 的支持，使得 PyTorch 用户也能利用 TensorBoard 的强大功能来可视化训练过程中的各种指标，包括标量、图像、图结构等。

`writer.add_image` 的具体作用包括：

**参数**

- **tag** (string): 图像的唯一标识符，用于在 TensorBoard 的界面中组织和区分不同的图像。
- **img_tensor** (torch.Tensor 或 numpy.ndarray): 要可视化的图像数据。它应该是一个四维的 PyTorch Tensor（对于批量图像）或一个三维的 NumPy 数组（HWC 格式，即高度、宽度、通道数），且通道数应该在最后一个维度上。对于单个图像，PyTorch Tensor 通常是 `[C, H, W]` 形状，而 NumPy 数组是 `[H, W, C]` 形状。TensorBoard 要求图像数据是浮点类型（通常是 `float32` 或 `float64`），并且值域应该在 `[0.0, 1.0]` 或 `[-1.0, 1.0]` 范围内（取决于你的数据和可视化需求）。
- **global_step** (int, 可选): 训练的全局步长（或迭代次数）。这个参数用于在 TensorBoard 的界面中组织数据，使得用户可以按照训练进度查看图像的变化。如果未指定，则默认为 `writer` 的当前全局步长（如果有的话）。
- **walltime** (float, 可选): 记录这个事件的时间戳（以秒为单位，从 Unix 纪元开始）。这通常用于记录实际发生事件的时间，而不是仅仅依赖于迭代次数。如果未指定，则默认使用当前时间。

### 9.writer.add_images()

在 PyTorch 的 `torch.utils.tensorboard.SummaryWriter` 中，`add_images()` 方法用于将图像数据记录到 TensorBoard 中，以便进行可视化。然而，需要注意的是 `add_images()` 方法的使用方式可能与你最初的想法有所不同，特别是当你尝试直接传递一个包含多个图像的批次（batch）时。

`add_images()` 方法通常期望的输入是一个图像张量列表（list of tensors），其中每个张量代表一个单独的图像，或者是一个包含多个图像（每个图像是一个通道数、高度和宽度的三维张量）的单个四维张量（batch_size, channels, height, width），但后者在较新版本的 PyTorch 中可能不被直接支持，或者其行为可能不是你所期望的。

如果你的 `imgs` 是一个批次（即四维张量），并且你想要为每个图像分别记录到 TensorBoard，你需要遍历这个批次，并对每个图像单独调用 `add_image()`（注意是 `add_image()` 而不是 `add_images()`，尽管名字相似但用法不同）。

## 4.Transforms的使用

### 4.1 transforms结构及用法

![image-20240801145416501](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240801145416501.png)

![image-20240801150547235](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240801150547235.png)

### 4.2 代码实现

```python
from torchvision import transforms
from PIL import Image
import cv2
from torch.utils.tensorboard import SummaryWriter
#python的用法 -> tensor数据类型
#通过transforms.ToTensor去看两个问题
# 2.为什么我们需要Tensor数据类型
img_path = "C:\\pythonProject3\\pytorch\\data\\train\\ants_image\\0013035.jpg"
img = Image.open(img_path)

writer = SummaryWriter("logs")
# 1.transforms如何使用
tensor_trans = transforms.ToTensor()
tensor_img = tensor_trans(img)
print(tensor_img)

writer.add_image("Tensor_img",tensor_img)
writer.close()
```

### 4.3 transforms中为什么需要转变成Tensor数据类型

1. **与PyTorch的兼容性**：
   PyTorch的神经网络和数据处理都是基于Tensor的。为了能够将预处理后的图像输入到神经网络中进行训练和推理，这些数据首先需要被转换成Tensor格式。这是因为PyTorch的神经网络层和其他相关操作都是设计为接受Tensor作为输入的。
2. **自动微分**：
   如前所述，PyTorch的Tensor是构建在自动微分系统之上的。将图像转换成Tensor后，可以利用PyTorch的自动微分功能来计算梯度，这对于神经网络的训练是必不可少的。尽管在图像转换到Tensor的过程中不直接涉及梯度的计算，但这一步是准备数据以便后续训练过程中使用自动微分的前提。
3. **GPU加速**：
   Tensor可以在GPU上高效运行，这显著提高了大规模数据处理的性能。通过将图像转换成Tensor，我们可以轻松地将其转移到GPU上，以加速神经网络的训练和推理过程。
4. **数据一致性**：
   在深度学习中，数据的一致性是非常重要的。将图像转换成Tensor不仅意味着将数据的类型进行了统一（即都是Tensor），还通常伴随着数据范围的标准化（例如，将像素值从[0, 255]缩放到[0.0, 1.0]）。这种数据一致性有助于神经网络的训练，因为它减少了由于不同数据源或不同预处理步骤导致的数据偏差。
5. **方便的数据处理**：
   PyTorch的`transforms`模块提供了一系列用于图像预处理和数据增强的操作，这些操作都是设计为对Tensor进行操作的。通过将图像转换成Tensor，我们可以直接应用这些`transforms`，而无需编写额外的代码来处理不同类型的数据。
6. **简洁的API**：
   PyTorch的API设计得非常简洁和直观。通过将图像转换成Tensor，我们可以使用PyTorch提供的丰富功能，如模型定义、损失函数计算、优化器设置等，而无需担心数据类型的不匹配或额外的转换步骤。

### 4.4 transforms.ToTensor()

在PyTorch中定义了一个转换（transform），该转换的作用是将PIL图像或者NumPy ndarray（满足一定的条件，比如数据类型和值域）转换成PyTorch的Tensor。

## 5.常见的Transforms

### 5.1 输入

PIL  --->  Image.open()

`transforms`模块中的转换可以接受多种类型的输入，但最常见的是PIL图像（`PIL.Image.Image`）和NumPy数组（`numpy.ndarray`）。这些输入代表了待处理的图像数据。

### 5.2 输出

tensor  --->  ToTensor()

转换的输出通常是PyTorch的Tensor，它包含了处理后的图像数据。这个Tensor可能已经被归一化、缩放、裁剪或进行了其他形式的变换，具体取决于应用了哪些转换。

### 5.3 作用

narrays ---> cv.imread()

### 5.4 Resize()的使用

`Resize()`是一个非常常用的转换（transform），它用于调整图像的大小。这个转换接受一个元组`(size)`作为参数，其中`size`可以是单个整数或者一个包含两个整数的元组。

- 如果`size`是一个整数，那么图像将被等比例缩放，使得图像的短边（高度或宽度中较小的那个）等于`size`指定的长度，而长边则按比例缩放。
- 如果`size`是一个包含两个整数的元组`(h, w)`，那么图像将被直接缩放到这个新的高度`h`和宽度`w`，这可能会导致图像的宽高比发生变化。

eg: `resize_transform = transforms.Resize((256, 256))`

- `Resize()`转换返回的是一个PIL Image对象（如果输入也是PIL Image的话）。如果你想要一个Tensor作为输出，你需要在`Resize()`之后添加`transforms.ToTensor()`转换。

### 5.5 Compose()的使用

`Compose()`是一个非常有用的类，它允许你将多个转换（transforms）组合成一个单一的转换流程。这对于图像预处理和数据增强特别有用，因为它允许你以特定的顺序应用多个转换步骤。

- `Compose()`中的转换将按照你传递给它的顺序被应用。因此，请确保你按照正确的顺序排列它们。
- 你可以将任意数量的转换添加到`Compose()`中，但请注意，某些转换可能要求特定的输入类型（如PIL Image或Tensor）。如果转换之间的输入类型不匹配，你可能需要添加额外的转换来确保类型兼容性。
- 在使用`Compose()`时，你不需要担心转换之间的状态管理或依赖关系。`Compose()`会为你处理这些细节，确保每个转换都能接收到正确的输入。
- `Compose()`是PyTorch数据加载和预处理流程中的一个关键组件，它使得数据预处理过程更加模块化和灵活。通过组合不同的转换，你可以轻松地创建出满足你特定需求的数据预处理流程。

eg:

```py
# 定义转换列表  
transform_list = [  
    transforms.ToTensor(),  # 将PIL Image或numpy.ndarray转换为Tensor，并归一化到[0.0, 1.0]  
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])  # 对Tensor进行标准化处理  
]  
  
# 使用Compose组合这些转换
transform = transforms.Compose(transform_list)  
```

### 5.6 RandomCrop()的用法

`RandomCrop()`是一个用于随机裁剪图像的转换（transform）。这个转换可以从输入图像中随机裁剪出一个指定大小的区域，这有助于数据增强，因为模型在训练过程中会看到图像的不同部分。

`RandomCrop()`接受几个参数，但最重要的是`size`参数，它指定了裁剪区域的大小。`size`可以是一个整数，表示裁剪区域将是正方形，且边长为`size`指定的值；或者，它也可以是一个包含两个整数的元组`(height, width)`，表示裁剪区域的高度和宽度。

除了`size`之外，`RandomCrop()`还接受其他可选参数，如`padding`（在裁剪前在图像周围添加的填充大小）、`padding_mode`（填充模式，如`'constant'`、`'edge'`、`'reflect'`或`'symmetric'`）、`fill`（当`padding_mode='constant'`时使用的填充值）以及`padding_if_needed`（如果图像太小，是否需要先添加填充以使其能够进行裁剪）。

eg:

```py
from torchvision import transforms  
  
# 创建一个RandomCrop转换，裁剪大小为224x224  
random_crop_transform = transforms.RandomCrop(224)  
  
# 或者，指定裁剪区域的高度和宽度  
# random_crop_transform = transforms.RandomCrop((224, 299))  
  
# 假设你有一个PIL Image对象，名为image  
# 应用RandomCrop转换  
cropped_image = random_crop_transform(image)  
  
# 现在，cropped_image是一个PIL Image对象，它是从原始图像中随机裁剪出的224x224区域
```

- 如果原始图像的大小小于`RandomCrop()`指定的裁剪大小，那么默认情况下，这个转换会抛出一个错误。你可以通过设置`padding_if_needed=True`来允许在裁剪前自动添加填充（padding），但这可能会改变图像的原始内容。
- `RandomCrop()`是数据增强中常用的一个转换，因为它可以帮助模型学习到图像的不同部分，从而提高模型的泛化能力。

### 5‌.7 Normalize()的使用

`Normalize()`是一个用于标准化图像数据的转换（transform）。它通过对图像Tensor的每个通道进行归一化操作，使得模型的训练过程更加稳定和高效。标准化通常涉及减去均值（mean）并除以标准差（std），这样可以将数据缩放到一个较小的范围内，通常是[-1, 1]或[0, 1]，具体取决于均值和标准差的值。

`Normalize()`接受两个主要参数：`mean`和`std`。

- `mean`：一个序列，包含了每个通道的均值。对于RGB图像，这通常是一个包含三个元素的序列（或Tensor），分别对应R、G、B三个通道的均值。
- `std`：一个序列，包含了每个通道的标准差。与`mean`类似，对于RGB图像，这也是一个包含三个元素的序列（或Tensor）。

这两个参数可以是单个数值（表示所有通道共享相同的均值和标准差），也可以是一个序列（表示每个通道有其独特的均值和标准差）。

eg:

```py
from torchvision import transforms  
  
# 定义Normalize转换，这里以ImageNet数据集的均值和标准差为例  
normalize_transform = transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])  
  
# 假设你已经有了一个Tensor image，其形状为[C, H, W]，其中C是通道数，H是高度，W是宽度  
# 应用Normalize转换  
normalized_image = normalize_transform(image)  
  
# 注意：通常Normalize转换会与其他转换（如ToTensor）一起使用，因为Normalize需要Tensor作为输入  
# 下面是一个完整的转换流程示例  
transform = transforms.Compose([  
    transforms.ToTensor(),  # 将PIL Image或numpy.ndarray转换为Tensor  
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])  # 对Tensor进行标准化处理  
])  
  
# 假设你有一个PIL Image对象，名为image  
# 应用组合转换  
transformed_tensor = transform(image)  
  
# 现在，transformed_tensor是一个经过ToTensor和Normalize转换的Tensor
```



### 5.8 代码实现

```python
from PIL import Image
from torchvision import transforms
from torch.utils.tensorboard import SummaryWriter
img = Image.open('C:\\pythonProject3\\pytorch\\data\\train\\ants_image\\0013035.jpg')
print(img)
# ToTensor
writer = SummaryWriter("logs")
trans_totensor = transforms.ToTensor()
img_tensor = trans_totensor(img)
writer.add_image('ToTensor', img_tensor)
writer.close()
# Normalize
print(img_tensor[0][0][0])
trans_norm = transforms.Normalize([0.5, 0.5, 0.5],[0.5, 0.5, 0.5])
img_norm = trans_norm(img_tensor)
print(img_norm[0][0][0])
writer.add_image('Normalization', img_norm)
writer.close()
#Resize
print(img.size)
trans_resize = transforms.Resize((512,512))
# img PIL-> resize -> img_resize PIL
img_resize = trans_resize(img)
img_resize = trans_totensor(img_resize)
writer.add_image('Resize', img_resize,0)
print(img_resize)
# compose - resize - 2
trans_resize_2 = transforms.Resize(512)
# PIL -> PIL -> tensor
trans_compose = transforms.Compose([trans_resize_2, trans_totensor])
img_resize_2 = trans_compose(img)
writer.add_image('Compose', img_resize_2,1)
writer.close()
#RandomCrop
trans_random = transforms.RandomCrop(512)
trans_compose_2 = transforms.Compose([trans_random, trans_totensor])
for i in range(10):
    img_crop = trans_compose_2(img)
    writer.add_image('RandomCrop', img_crop,i)

writer.close()
```

## 6.python中`__call__`的用法

**使用 call 方法可以使类的实例具有可调用的特性，使得类的实例可以像函数一样被调用**

### 6.1代码实现

```python
class Person:
    def __call__(self, name):
        print("__call__" + "Hello" + name)
 
    def hello(self,name):
        print("hello" + name)
 
person = Person()
person("zhangsan")
person.hello("lisi")
 
print(callable(person)) # True
# 运行结果
__call__Hellozhangsan
hellolisi
```

## 7.torchvision中的数据集使用

### 7.1 代码实现

```python
import torchvision
from torch.utils.tensorboard import SummaryWriter

dataset_transform = torchvision.transforms.Compose(
    [
        torchvision.transforms.ToTensor()
    ]
)
train_set = torchvision.datasets.CIFAR10(root='./dataset', train=True, transform=dataset_transform,download=True)
test_set = torchvision.datasets.CIFAR10(root='./dataset', train=False, transform=dataset_transform,download=True)

# print(test_set[0])
# print(test_set.classes)
# img,target = test_set[0]
# print(img)
# print(target)
# print(test_set.classes[target])
# img.show()

# print(test_set[0])
writer = SummaryWriter("p10")
for i in range(10):
    img,target = test_set[i]
    writer.add_image("test_set",img,i)
writer.close()
```

### 7.2 torchvision.datasets.CIFAR10的介绍

`torchvision.datasets.CIFAR10` 是 `torchvision` 库中的一个类，用于加载 CIFAR-10 数据集。CIFAR-10 是一个常用的计算机视觉数据集，包含了 60000 张 32x32 的彩色图像，这些图像被分为 10 个类别，每个类别有 6000 张图像。这个数据集广泛用于图像识别、分类等任务的训练和测试。

当你使用 `torchvision.datasets.CIFAR10` 时，你实际上是在执行以下操作：

1. **下载数据集**（如果尚未下载）：如果你设置了 `download=True`，并且指定的 `root` 目录下没有 CIFAR-10 数据集，那么 `torchvision` 会自动从互联网上下载数据集并存储在你指定的 `root` 目录下。
2. **加载数据集**：一旦数据集下载或确认存在于 `root` 目录下，`torchvision.datasets.CIFAR10` 就会加载数据集。你可以通过 `train=True` 来加载训练集，或者通过 `train=False` 来加载测试集。
3. **应用数据变换**：你可以通过 `transform` 参数来指定一系列的数据预处理和增强操作。这些操作会在数据加载时自动应用于每个图像样本上。例如，你可以使用 `ToTensor()` 变换将 PIL 图像或 NumPy ndarray 转换为 PyTorch Tensor，或者使用 `Normalize()` 变换来对 Tensor 进行归一化处理。
4. **提供数据加载接口**：加载完成后，`CIFAR10` 对象提供了一个迭代器接口，允许你通过索引访问数据集中的图像和标签，或者与 PyTorch 的 `DataLoader` 结合使用，以批量加载数据的方式进行训练或测试。

### 7.3 torchvision.datasets.CIFAR10的使用

通过 `root` 参数指定数据集的存储位置，`train` 参数控制是加载训练集还是测试集，`download` 参数控制是否需要从互联网下载数据集（如果数据集已经下载过，再次设置 `download=True` 也不会重复下载），`transform` 参数则应用了我们之前定义的数据变换。

## 8.DataLoader的使用

`DataLoader` 是 PyTorch 中用于数据加载的一个重要类，它结合了数据集（`Dataset`）和采样器（`Sampler`），能够提供一个可迭代的、高效的数据加载方式，特别适合用于深度学习模型的训练。`DataLoader` 支持自动批处理、打乱数据、多进程数据加载等功能，可以显著提高数据处理的效率和灵活性。

**基本使用**

首先，你需要有一个继承自 `torch.utils.data.Dataset` 的数据集类，该类需要实现两个方法：`__len__()` 和 `__getitem__()`。`__len__()` 方法返回数据集中的样本数量，而 `__getitem__()` 方法根据索引返回相应的样本及其标签（如果有的话）。

![image-20240804172731053](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240804172731053.png)

![image-20240804174808242](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240804174808242.png)

### 8.1 代码实现

```python
import torchvision
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter

# 准备的测试数据集
test_data = torchvision.datasets.CIFAR10(root='./dataset', train=False, transform=torchvision.transforms.ToTensor())
test_loader = DataLoader(dataset=test_data, batch_size=64, shuffle=True, num_workers=0, drop_last=False)
# 测试数据集中第一张图片及target
img,target = test_data[0]
writer = SummaryWriter('dataloader')
for epoch in range(2):
    step = 0
    for data in test_loader:
        imgs,targets = data
        # print(img.shape)
        # print(target)
        writer.add_images("test_data",imgs,step)
        step += 1
writer.close()
```

### 8.2 创建DataLoader

```py
test_loader = DataLoader(dataset=test_data, batch_size=64, shuffle=True, num_workers=0, drop_last=False)
```

- 使用`DataLoader`来包装`test_data`，以便进行批量加载和迭代。
- `batch_size=64`表示每个批次加载64张图片。
- `shuffle=True`表示在每个epoch开始时打乱数据。但在测试数据集中，这通常不是必需的，但这里为了示例保持一致性。
- `num_workers=0`表示不使用多进程来加载数据（使用主进程加载）。
- `drop_last=False`表示如果数据集大小不能被`batch_size`整除，则保留最后一个不完整的批次。

## 9.神经网络的基本骨架-nn.Module的使用

在PyTorch中，`nn.Module`是所有神经网络模块的基类，它为构建神经网络提供了基本骨架。使用`nn.Module`，你可以定义自己的神经网络层、自定义模块以及整个神经网络架构。这里将详细解释`nn.Module`的使用以及如何利用它来构建神经网络。

### 1. 继承`nn.Module`

首先，你需要定义一个继承自`nn.Module`的类。在这个类中，你可以定义网络所需的层（如全连接层、卷积层等）以及网络的前向传播逻辑。

```py
import torch.nn as nn  
  
class MyNet(nn.Module):  
    def __init__(self):  
        super(MyNet, self).__init__()  # 调用父类的构造函数  
        # 定义网络的层  
        self.fc1 = nn.Linear(in_features=10, out_features=50)  # 定义一个全连接层  
        self.relu = nn.ReLU()  # 定义ReLU激活函数  
        self.fc2 = nn.Linear(in_features=50, out_features=10)  # 再定义一个全连接层  
  
    def forward(self, x):  
        # 定义前向传播逻辑  
        x = self.fc1(x)  
        x = self.relu(x)  
        x = self.fc2(x)  
        return x
```

在上面的例子中，`MyNet`类定义了一个简单的神经网络，它包含两个全连接层和一个ReLU激活函数。`__init__`方法用于初始化网络中的层，而`forward`方法则定义了数据通过网络的前向传播路径。

### 2. 实例化模块并调用前向传播

一旦你定义了继承自`nn.Module`的类，就可以创建该类的实例（即网络模型），并使用它来执行前向传播。

```py
# 创建MyNet的实例  
net = MyNet()  
  
# 创建一个随机的输入张量  
input_tensor = torch.randn(1, 10)  # 假设输入维度是(batch_size, input_features) = (1, 10)  
  
# 执行前向传播  
output = net(input_tensor)  
  
print(output)
```

### 3. 模型的参数

`nn.Module`的子类会自动管理其内部定义的层的参数（如权重和偏置）。你可以通过`parameters()`或`named_parameters()`方法来访问这些参数。

### 4. 模型的训练

虽然`nn.Module`本身并不直接提供训练功能，但它是构建可训练模型的基础。在PyTorch中，训练模型通常涉及定义损失函数、优化器以及编写训练循环来更新模型的参数。

![image-20240806180423672](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240806180423672.png)

![image-20240806180752087](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240806180752087.png)

代码实现：

```python
import torch.nn as nn
import torch

class Tudui(nn.Module):
    def __init__(self):
        super().__init__()
    def forward(self, input):
        output = input + 1
        return output

tudui = Tudui()
x = torch.tensor(1.0)
output = tudui(x)
print(output)
```

### 9.1`__init__` 方法

在`Tudui`类中，我们首先定义了`__init__`方法。这是Python中类的初始化方法，当创建类的新实例时会自动调用它。在`Tudui`类中，`__init__`方法的作用主要是调用父类`nn.Module`的`__init__`方法

```py
def __init__(self):  
        super().__init__()
```

- `super()`函数返回了一个代表父类（在这个例子中是`nn.Module`）的临时对象，允许我们调用父类的方法。
- `__init__()`是父类`nn.Module`的初始化方法，它负责设置一些与模型相关的内部状态和属性。通过调用它，我们确保了`Tudui`类的实例能够继承和使用`nn.Module`的所有功能。

### 9.2 `forward` 方法

`forward`方法是定义模型前向传播逻辑的地方。在PyTorch中，当你调用模型实例（即`nn.Module`的子类实例）时，实际上是在调用它的`forward`方法

```py
def forward(self, input):  
        output = input + 1  
        return output
```

- `forward`方法接收一个参数`input`，这是模型的输入数据。在PyTorch中，这些数据通常是以张量（Tensor）的形式存在的。
- 在`forward`方法的内部，我们定义了一个名为`output`的变量，它通过将输入`input`与数字`1`相加得到。这个操作是模型的前向传播逻辑，它表示了模型如何处理输入数据并产生输出。
- 最后，`forward`方法返回了`output`变量，即模型的输出

## 10.卷积操作

![image-20240806185646033](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240806185646033.png)

![image-20240806191700652](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240806191700652.png)

代码实现：

```python
import torch
import torch.nn.functional as f
input = torch.tensor([[1,2,0,3,1],
                     [0,1,2,3,1],
                    [1,2,1,0,0],
                     [5,2,3,1,1],
                     [2,1,0,1,1]])
kernel = torch.tensor([[1,2,1],
                       [0,1,0],
                       [2,1,0]])
input = torch.reshape(input,(1,1,5,5))
kernel = torch.reshape(kernel,(1,1,3,3))
print(input.shape)
print(kernel.shape)
output = f.conv2d(input,kernel,stride=1,padding=0)
print(output)
output2 = f.conv2d(input,kernel,stride=2,padding=0)
print(output2)
output3 = f.conv2d(input,kernel,stride=1,padding=1)
print(output3)
```

### 10.1 代码解释

### 第一步：导入必要的库

```py
import torch  
import torch.nn.functional as f
```

- `torch` 是PyTorch的主库，提供了许多用于张量（多维数组）操作的功能。
- `torch.nn.functional` 包含了PyTorch中定义的所有神经网络相关的函数，例如卷积、池化等。这里，我们通过 `f` 来引用它，以简化对函数的调用。

### 第二步：定义输入和卷积核

```py
input = torch.tensor([[1,2,0,3,1],  
                     [0,1,2,3,1],  
                     [1,2,1,0,0],  
                     [5,2,3,1,1],  
                     [2,1,0,1,1]])  
kernel = torch.tensor([[1,2,1],  
                       [0,1,0],  
                       [2,1,0]])
```

- `input` 是一个5x5的二维张量，代表了一个简单的二维图像数据。
- `kernel` 是一个3x3的二维张量，用作卷积操作的卷积核。

### 第三步：调整输入和卷积核的形状

```py
input = torch.reshape(input,(1,1,5,5))  
kernel = torch.reshape(kernel,(1,1,3,3))
```

- 在PyTorch中，二维卷积函数 `f.conv2d` 需要特定的输入形状：`(N, C_in, H, W)`，其中 `N` 是批次大小，`C_in` 是输入通道数，`H` 和 `W` 分别是输入的高度和宽度。
- 类似地，卷积核也需要有形状 `(out_channels, in_channels, kernel_height, kernel_width)`。
- 我们将 `input` 调整为 `(1, 1, 5, 5)`，表示有1个批次，1个输入通道，高度和宽度都是5。
- 我们将 `kernel` 调整为 `(1, 1, 3, 3)`，表示输出通道数为1，输入通道数为1，卷积核的高度和宽度都是3。

### 第四步：执行卷积操作

```py
output = f.conv2d(input,kernel,stride=1,padding=0)
```

- 这里，我们使用 `f.conv2d` 执行卷积操作，其中 `stride=1` 表示卷积核每次移动的步长为1，`padding=0` 表示在输入周围不添加任何填充。
- 输出 `output` 的形状将取决于输入形状、卷积核大小和步长、填充大小。在这种情况下，输出形状为 `(1, 1, 3, 3)`，因为 `5x5` 的输入在步长为1且无填充的情况下，经过 `3x3` 的卷积核后，高度和宽度都会减少 `(3-1)=2`，从而变为 `3x3`。

## 11.神经网络--卷积层

卷积层在CNN中起着至关重要的作用，它不仅能够提取输入数据的特征，还能够通过参数共享和稀疏连接机制降低模型的复杂度和计算量，同时增强模型的鲁棒性和平移不变性

代码实现：

```python
import torch
import torchvision
from torch import nn
from torch.nn import Conv2d
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter

dataset = torchvision.datasets.CIFAR10("C:\\pythonProject3\\pytorch\\dataset", train=False, transform=torchvision.transforms.ToTensor(), download=True)
dataloader = DataLoader(dataset, batch_size=64)
writer = SummaryWriter('logs')
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.conv1 = nn.Conv2d(in_channels=3, out_channels=6, kernel_size=3,stride=1, padding=0)
    def forward(self, x):
        x = self.conv1(x)
        return x
tudui = Tudui()
print(tudui)
step = 0
for data in dataloader:
    imgs,targets = data
    output = tudui(imgs)
    print(imgs.shape)
    print(output.shape)
    writer.add_images("input", imgs,step)
    output = torch.reshape(output,(-1,3,30,30))
    writer.add_images("output",output,step)
    step = step + 1
```

### 11.1 nn.Conv2d()

`nn.Conv2d()` 的主要作用是对输入数据进行二维卷积操作。在图像处理中，这通常意味着对图像的每个通道（对于彩色图像，通常是RGB三个通道）应用一组可学习的滤波器（或称为卷积核），以提取图像中的特征。这些特征可以是边缘、纹理等，它们对于后续的图像识别或分类任务非常有用。

`nn.Conv2d()` 的基本使用方式如下：

```py
import torch  
import torch.nn as nn  
  
# 定义一个二维卷积层  
conv_layer = nn.Conv2d(in_channels, out_channels, kernel_size, stride=1, padding=0, dilation=1, groups=1, bias=True, padding_mode='zeros')
```

其中参数的含义如下：

- `in_channels` (int) – 输入信号的通道数。例如，对于RGB图像，这个值就是3。
- `out_channels` (int) – 卷积产生的通道数。这个值决定了输出数据的深度（或称为卷积核的数量）。
- `kernel_size` (int 或 tuple) – 卷积核的大小。可以是单个整数（表示卷积核的高度和宽度相同），也可以是一个整数元组（表示卷积核的高度和宽度可能不同）。
- `stride` (int 或 tuple, 可选) – 卷积的步长。与 `kernel_size` 类似，可以是单个整数或整数元组。
- `padding` (int 或 tuple, 可选) – 输入的每一边将添加的零填充的数量。这有助于控制输出特征图的大小。
- `dilation` (int 或 tuple, 可选) – 卷积核元素之间的间距。
- `groups` (int, 可选) – 控制输入和输出之间的连接。`groups=1` 时，输出是所有输入通道的卷积的集合。`groups=2` 时，输入和输出通道被分成两半，并且每个输出通道组仅与输入通道组的一半连接。
- `bias` (bool, 可选) – 如果为 `True`，则向输出添加可学习的偏置项。
- `padding_mode` (str, 可选) – 填充模式，默认为 `'zeros'`。还可以是 `'reflect'`、`'replicate'` 或 `'circular'`

## 12.神经网络--最大池化的使用

最大池化（Max Pooling）是卷积神经网络（CNN）中常用的一种池化操作，它用于降低特征图（feature maps）的维度（主要是宽度和高度），从而减少网络中的参数数量和计算量，同时也有助于防止过拟合。

![image-20240808163844917](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240808163844917.png)

代码实现

```python
import torch
from torch import nn
from torch.nn import MaxPool2d
import torchvision
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter
dataset = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=False, download=True,transform=torchvision.transforms.ToTensor())
dataloader = DataLoader(dataset, batch_size=64)
#input = torch.tensor([[1,2,0,3,1],
                      #[0,1,2,3,1],
                      #[1,2,1,0,0],
                      #[5,2,3,1,1],
                      #[2,1,0,1,1]],dtype=torch.float32)
#input = torch.reshape(input,(-1,1,5,5))
#print(input.shape)
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.maxpool = nn.MaxPool2d(kernel_size=3,ceil_mode=False)

    def forward(self, input):
        output = self.maxpool(input)
        return output

tudui = Tudui()
#output = tudui(input)
#print(output)
writer = SummaryWriter('logs_maxpool')
step = 0
for data in dataloader:
    imgs,targets = data
    writer.add_images('input',imgs,step)
    output = tudui(imgs)
    writer.add_images('output',output,step)
    step += 1
writer.close()
```

### 12.1 nn.MaxPool2d()

`nn.MaxPool2d`是一个二维最大池化层，它用于对输入的特征图（feature maps）进行下采样。这个层会独立地在每个输入通道（channel）上滑动一个窗口（kernel），并在每个窗口内选择最大值作为输出。这对于减少特征图的尺寸（在高度和宽度上）、降低计算量、提取最重要的特征以及增加特征的平移不变性非常有用。

```py
self.maxpool = nn.MaxPool2d(kernel_size=3, ceil_mode=False)
```

这行代码定义了一个二维最大池化层，其参数说明如下：

- `kernel_size=3`：指定了池化窗口的大小为3x3。这意味着在每个通道上，将有一个3x3的窗口滑动过特征图，并在每个这样的窗口中选取最大值。
- `ceil_mode=False`：这个参数控制池化操作后输出尺寸的计算方式。当`ceil_mode=False`时（默认值），输出尺寸的计算会向下取整。具体来说，对于每个维度（高度和宽度），输出尺寸的计算公式是`(输入尺寸 - kernel_size + 2*padding) / stride + 1`，其中`stride`是步长（默认为`kernel_size`），`padding`是填充大小（默认为0）。由于默认`stride=kernel_size`且`padding=0`，所以输出尺寸会小于输入尺寸（在`ceil_mode=False`的情况下）。如果设置为`True`，则使用向上取整来计算输出尺寸，这可能会导致输出尺寸在某些情况下比预期的大。

## 13.神经网络--非线性激活

非线性激活函数（Non-linear Activation Functions）扮演着至关重要的角色。这些函数的主要目的是在神经网络的各层之间引入非线性，使得网络能够学习并表示复杂的非线性关系。

![image-20240808172055465](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240808172055465.png)

代码实现

```python
import torch
import torchvision
from torch import nn
from torch.nn import ReLU
from torch.nn import Sigmoid
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter

input = torch.tensor([[1,-0.5],
                     [-1,3]])
output = torch.reshape(input,(-1,1,2,2))
print(output.shape)
dataset = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=False, download=True,transform=torchvision.transforms.ToTensor())
dataloader = DataLoader(dataset, batch_size=64)
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui,self).__init__()
        self.relu1 = ReLU()
        self.sigmoid1 = Sigmoid()

    def forward(self,input):
        output = self.sigmoid1(input)
        return output
tudui = Tudui()
writer = SummaryWriter('logs_relu')
step = 0
for data in dataloader:
    imgs,targets = data
    writer.add_images("input",imgs,global_step=step)
    output = tudui(imgs)
    writer.add_images("output",output,global_step=step)
    step += 1
writer.close()
```

### 13.1 常见的非线性激活函数

1. **Sigmoid**：Sigmoid函数将任意实数值映射到(0, 1)区间，常用于二分类问题的输出层。然而，由于其梯度饱和问题（当输入值远离0时，梯度接近0），它在使用多层网络时可能会导致梯度消失问题。
2. **Tanh（双曲正切）**：Tanh函数将任意实数值映射到(-1, 1)区间，并以0为中心。它类似于Sigmoid函数，但在实际应用中通常比Sigmoid函数表现更好，因为它关于原点对称，有助于加速收敛。然而，它同样存在梯度饱和问题。
3. **ReLU（线性修正单元）**：ReLU函数是目前最常用的激活函数之一。它将所有负值置为0，正值保持不变。ReLU函数计算简单，能够缓解梯度消失问题（在正区间内），并加速网络训练。然而，它可能导致神经元死亡（即某些神经元永远不会激活），这被称为“ReLU死亡”问题。
4. **Leaky ReLU、PReLU（参数化ReLU）、ELU（指数线性单元）**：这些是对ReLU函数的改进版本，旨在解决ReLU死亡问题。它们允许小的负梯度通过，从而避免神经元完全失活。
5. **Softmax**：虽然Softmax通常被视为一种特殊的激活函数，用于多分类问题的输出层，但它也引入了非线性。Softmax函数将输出转换为概率分布，使得所有输出值的和为1，并且每个输出值都在(0, 1)区间内。

### 13.2 激活函数的选择

选择哪种激活函数取决于具体的应用场景和神经网络的结构。例如，对于二分类问题，Sigmoid或Softmax可能是合适的输出层激活函数。对于隐藏层，ReLU及其变体（如Leaky ReLU、PReLU）因其计算效率和缓解梯度消失问题的能力而广受欢迎。

### 13.3 ReLU()

ReLU（Rectified Linear Unit，线性修正单元）是一种非常流行的激活函数，它被广泛用于神经网络中。ReLU函数的主要作用是将所有的负值置为0，而正值保持不变，这有助于引入非线性，同时避免了梯度消失问题（在正值区间内）。

```py
# 创建ReLU激活函数的实例，并将其赋值给self.relu1  
self.relu1 = nn.ReLU()  # 注意这里使用了括号来实例化ReLU
x = self.relu1(x)  # 通过self.relu1应用ReLU激活函数 
```

### 13.4 sigmoid()

`sigmoid()` 函数通常是通过 `torch.sigmoid()` 来调用的，它不接受类实例的方式（如 `self.sigmoid = Sigmoid()` 这样的写法在PyTorch中是不常见的，因为PyTorch的激活函数大多是通过`torch.nn.functional`模块以函数的形式提供的）。

```py
import torch  
  
# 假设有一个tensor  
x = torch.randn(1, 5)  # 随机生成一个1x5的tensor  
  
# 直接使用torch.sigmoid()函数  
y = torch.sigmoid(x)  
  
print(y)  # 输出经过sigmoid函数处理后的tensor
```

## 14.神经网络--线性层及其他层介绍

![image-20240808180125956](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240808180125956.png)

代码实现

```python
import torch
import torchvision
from torch import nn
from torch.nn import Linear
from torch.utils.data import DataLoader
dataset = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=False,download=True,transform=torchvision.transforms.ToTensor())
dataloader = DataLoader(dataset,batch_size=64,drop_last=True)
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.linear1 = Linear(196608,10)

    def forward(self,x):
        output = self.linear1(x)
        return output
tudui =  Tudui()

for data in dataloader:
    imgs,targets = data
    print(imgs.shape)
    #output = torch.reshape(imgs,(1,1,1,-1))
    output = torch.flatten(imgs)
    print(output.shape)
    output = tudui(output)
    print(output.shape)
```

### 14.1 Linear()的使用和作用

`Linear()`函数（实际上是`torch.nn.Linear`类的实例化）的使用和作用非常关键，尤其是在构建神经网络时。`Linear`层，也被称为全连接层或密集层，是神经网络中最基本的组件之一。

#### 14.1.1 使用

`Linear()`的使用非常简单，通常是通过传递两个参数来实例化：`in_features`和`out_features`。这两个参数分别代表输入特征的数量和输出特征的数量（或维度）。

```py
import torch.nn as nn  
  
# 实例化一个Linear层  
linear_layer = nn.Linear(in_features=10, out_features=5)
```

在这个例子中，`linear_layer`接收一个形状为`(batch_size, 10)`的输入张量，并输出一个形状为`(batch_size, 5)`的张量。`batch_size`是批处理中样本的数量，它可以在运行时动态变化。

#### 14.1.2 作用

`Linear()`层的作用是对输入数据进行线性变换。这种变换可以表示为：

output=input⋅*A**T*+*b*

其中：

- input 是形状为 `(batch_size, in_features)` 的输入张量。
- *A* 是形状为 `(out_features, in_features)` 的权重矩阵，它包含了从输入特征到输出特征的线性变换系数。
- *b* 是形状为 `(out_features,)` 的偏置向量，它包含了每个输出特征的偏置项。
- output 是形状为 `(batch_size, out_features)` 的输出张量。

在训练过程中，PyTorch会通过反向传播算法自动计算损失函数关于权重*A*和偏置*b*的梯度，并使用这些梯度来更新*A*和*b*的值，以便最小化损失函数。

## 15.搭建小实战和Sequential的使用

### 15.1 CIFAR 10 model 结构

![image-20240809163351391](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240809163351391.png)

### 15.2 nn.seq

```python
import torch
import torchvision
from torch import nn
from torch.nn import Conv2d
from torch.nn import MaxPool2d
from torch.nn import Flatten,Linear,Sequential
from torch.utils.tensorboard import SummaryWriter


class TUdui(nn.Module):
    def __init__(self):
        super(TUdui, self).__init__()
        #self.conv1 = Conv2d(3, 32, kernel_size=5,padding=2)
        #self.maxpool1 = MaxPool2d(2)
        #self.conv2 = Conv2d(32, 32, kernel_size=5,padding=2)
        #self.maxpool2 = MaxPool2d(2)
        #self.conv3 = Conv2d(32, 64, kernel_size=5,padding=2)
        #self.maxpool3 = MaxPool2d(2)
        #self.flatten = nn.Flatten()
        #self.linear1 = Linear(1024, 64)
        #self.linear2 = Linear(64, 10)
        self.module1 = Sequential(
            Conv2d(3, 32, kernel_size=5, padding=2),
            MaxPool2d(2),
            Conv2d(32, 32, kernel_size=5, padding=2),
            MaxPool2d(2),
            Conv2d(32, 64, kernel_size=5, padding=2),
            MaxPool2d(2),
            Flatten(),
            Linear(1024, 64),
            Linear(64, 10)
        )
    def forward(self,x):
        #x = self.conv1(x)
        #x = self.maxpool1(x)
        #x = self.conv2(x)
        #x = self.maxpool2(x)
        #x = self.conv3(x)
        #x = self.maxpool3(x)
        #x = self.flatten(x)
        #x = self.linear1(x)
        #x = self.linear2(x)
        x = self.module1(x)
        return x

tudui = TUdui()
print(tudui)
input = torch.ones(64,3,32,32)
output = tudui(input)
print(output.shape)
writer = SummaryWriter("logs_seq")
writer.add_graph(tudui, input)
writer.close()
```

这段代码定义了一个使用PyTorch框架的神经网络模型，该模型是通过`Sequential`容器按顺序堆叠多个层构成的。下面是对每一步的详细解释：

1. 初始化Sequential容器

   ：

   - `self.module1 = Sequential(...)`：这行代码创建了一个`Sequential`模块，它按照传递给它的层的顺序来构建模型。在PyTorch中，`Sequential`是一个有序容器，允许我们按照插入的顺序将模块堆叠起来。这里，它被用来定义模型`self.module1`。

2. 第一层：Conv2d(3, 32, kernel_size=5, padding=2)

   ：

   - 这是一个二维卷积层（`Conv2d`），用于提取输入图像的特征。参数`3`表示输入图像的通道数（对于RGB图像通常是3），`32`表示输出特征图的数量（即该层会生成32个特征图）。`kernel_size=5`指定了卷积核的大小为5x5，`padding=2`表示在输入图像的边缘周围添加2层零填充，以保持特征图的空间维度在卷积操作后不变（对于stride=1时）。

3. 第二层：MaxPool2d(2)

   ：

   - 这是一个最大池化层（`MaxPool2d`），用于下采样特征图，减少其空间维度（即高度和宽度）。`2`表示池化窗口的大小为2x2，步长默认为窗口大小，因此输出特征图的每个维度都将减半。

4. 第三层至第五层

   ：

   - 这些层与前面的卷积层和池化层类似，但有所不同的是，第三层卷积层`Conv2d(32, 32, kernel_size=5, padding=2)`的输入和输出特征图数量都是32，这意味着它进一步在相同的特征空间上提取特征。
   - 第四层是另一个`MaxPool2d(2)`，进一步下采样特征图。
   - 第五层`Conv2d(32, 64, kernel_size=5, padding=2)`将特征图的数量从32增加到64，以便在更抽象的特征空间上继续学习。

5. 第六层：Flatten()

   ：

   - 这个层将前面层输出的多维特征图（可能是一个三维张量，包括高度、宽度和特征图数量）展平成一个一维张量，以便可以输入到全连接层（`Linear`层）中。

6. 第七层：Linear(1024, 64)

   ：

   - 这是一个全连接层（`Linear`），它将输入（假设展平后的特征数量为1024，这个数字取决于前面层的输出尺寸和图像大小）转换为64个输出特征。这些特征可以被视为网络对输入图像的高级抽象表示。

7. 第八层：Linear(64, 10)

   ：

   - 这是另一个全连接层，它将64个特征转换为10个输出，通常对应于10个类别的分类任务的分数（或概率）。如果这是一个分类问题，比如识别10个不同的手写数字（如MNIST数据集），则这些输出将被用作预测结果。

### 15.3 Flatten()

`Flatten()` 在神经网络和深度学习框架中，如 TensorFlow 和 PyTorch，是一个非常重要的层（layer）或操作。它的主要作用是将多维的输入数据“展平”成一维数组（或者说是线性化），以便可以被全连接层（fully connected layers，也称为密集连接层或dense layers）等后续层处理。

当你有一个多维的输入数据（比如，图像数据在卷积神经网络（CNN）中经过多个卷积层和池化层处理后得到的数据），这些数据往往具有多个维度（例如，高度、宽度和通道数）。然而，全连接层期望的输入通常是一维的，因为全连接层中的每个神经元都与前一层的所有神经元相连接。因此，为了能够将这种多维数据输入到全连接层中，就需要使用 `Flatten()` 操作来将多维数据转换为一维数组。

### 15.4 sequential()

`Sequential()` 在深度学习框架中的作用主要是提供一个容器，用于按顺序堆叠多个网络层（layers）以构建神经网络模型。这种顺序模型（Sequential model）是构建神经网络的一种非常直观和常用的方式，尤其适用于那些层与层之间直接相连、没有复杂分支或跳跃连接的网络结构。

## 16.损失函数与反向传播

损失函数是衡量模型预测值与实际值之间差异的函数。在训练过程中，我们的目标是找到一组参数，使得损失函数的值最小化。

1. **均方误差（Mean Squared Error, MSE）**：常用于回归问题，计算预测值与实际值之差的平方的平均值。

   ![image-20240825153322918](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240825153322918.png)

   其中，*y**i* 是实际值，*y*^*i* 是预测值，*n* 是样本数量。

2. **交叉熵损失（Cross-Entropy Loss）**：常用于分类问题，特别是当输出层使用softmax激活函数时。它衡量的是两个概率分布之间的差异。

   ![image-20240825153411515](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240825153411515.png)

   

   其中，*M* 是类别数，*y**i*,*c* 是样本 *i* 是否属于类别 *c* 的真实标签（0或1），*y*^*i*,*c* 是样本 *i* 属于类别 *c* 的预测概率。

反向传播是一种在神经网络中计算梯度的方法，用于通过链式法则更新网络中的权重和偏置。它的基本步骤如下：

1. **前向传播**：首先，输入数据通过神经网络进行前向传播，计算每一层的输出，直到得到最终的预测值。

2. **计算损失**：使用损失函数计算预测值与实际值之间的差异。

3. **反向传播**：

   - **计算梯度**：从输出层开始，使用链式法则逐层计算损失函数关于每一层参数的梯度。
   - **更新参数**：使用梯度下降（或其他优化算法）更新每一层的权重和偏置，以减小损失函数的值。

   梯度下降的基本公式为：

   *θ*=*θ*−*α*（∂*θ*/∂*L*）

   其中，*θ* 是需要更新的参数（权重或偏置），*α* 是学习率，∂*θ*∂*L* 是损失函数关于参数 *θ* 的梯度。

通过重复前向传播、计算损失和反向传播的过程，神经网络能够逐渐学习到数据的特征，并优化其参数，从而提高模型的性能。

![image-20240810171923821](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240810171923821.png)

![image-20240810173425419](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240810173425419.png)

### 16.1 loss计算公式

![image-20240810180743326](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240810180743326.png)

### 16.2loss代码实现

```python
import torch
from torch.nn import L1Loss
from torch import nn
inputs = torch.tensor([1,2,3], dtype=torch.float32)
targets = torch.tensor([1,2,5], dtype=torch.float32)

inputs = torch.reshape(inputs,(1,1,1,3))
targets = torch.reshape(targets,(1,1,1,3))

loss = L1Loss(reduction='sum')
result = loss(inputs,targets)
loss_mse = nn.MSELoss()
result_mse = loss_mse(inputs,targets)
print(result)
print(result_mse)

x = torch.tensor([0.1,0.2,0.3])
y = torch.tensor([1])
x = torch.reshape(x,(1,3))
loss_cross = nn.CrossEntropyLoss()
result_cross = loss_cross(x,y)
print(result_cross)
```

### 16.3损失函数的使用

**1. 导入损失函数**

首先，你需要从`torch.nn`模块中导入你想要的损失函数。PyTorch提供了多种预定义的损失函数，如`MSELoss`（均方误差损失）、`CrossEntropyLoss`（交叉熵损失，通常用于多分类问题）、`L1Loss`（L1损失，即绝对值损失）等。

```py
import torch  
import torch.nn as nn  
  
# 导入损失函数  
loss_fn = nn.MSELoss()  # 例如，使用均方误差损失
```

**2. 准备输入和目标**

在训练过程中，你需要准备模型的输入（通常是特征数据）和目标（通常是标签或实际值）。这些数据应该被转换为PyTorch张量（Tensor）。

```py
# 假设的输入和目标  
inputs = torch.randn(10, 3)  # 假设有10个样本，每个样本有3个特征  
targets = torch.randn(10, 1)  # 假设有10个样本的目标值
```

**3. 前向传播**

在训练循环中，你需要将输入数据传递给模型进行前向传播，以获得预测值。

```py
# 假设有一个简单的模型  
model = nn.Linear(3, 1)  # 一个线性层，输入特征为3，输出特征为1  
  
# 前向传播  
predictions = model(inputs)
```

**4. 计算损失**

使用损失函数计算预测值和目标值之间的差异。

```py
# 计算损失  
loss = loss_fn(predictions, targets)
```

**5. 反向传播和优化**

在计算出损失之后，你需要进行反向传播来更新模型的参数。这通常是通过调用损失张量的`.backward()`方法来实现的，它会计算损失关于模型参数的梯度。然后，你可以使用优化器（如SGD、Adam等）来更新这些参数。

### 16.4loss_net

```python
import torchvision
from torch import nn
from torch.nn import Conv2d
from torch.nn import MaxPool2d
from torch.nn import Flatten,Linear,Sequential
from torch.utils.data import DataLoader
dataset = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=False, download=True,transform=torchvision.transforms.ToTensor())
dataloader = DataLoader(dataset,batch_size=64)
class TUdui(nn.Module):
    def __init__(self):
        super(TUdui, self).__init__()
        self.module1 = Sequential(
            Conv2d(3, 32, kernel_size=5, padding=2),
            MaxPool2d(2),
            Conv2d(32, 32, kernel_size=5, padding=2),
            MaxPool2d(2),
            Conv2d(32, 64, kernel_size=5, padding=2),
            MaxPool2d(2),
            Flatten(),
            Linear(1024, 64),
            Linear(64, 10)
        )

    def forward(self, x):
        x = self.module1(x)
        return x
loss = nn.CrossEntropyLoss()
tudui = TUdui()
for data in dataloader:
    imgs,targets = data
    outputs = tudui(imgs)
    result_loss = loss(outputs,targets)
    result_loss.backward()
    print("ok")
```

### 16.5nn.MSELoss()

`nn.MSELoss()` 的主要作用是计算预测值（通常是模型的输出）和真实值（也称为目标或标签）之间的均方误差。这个损失值越小，表示模型的预测越接近真实值，即模型的性能越好。

**使用**

使用 `nn.MSELoss()` 时，你需要遵循以下步骤：

1. **实例化**：首先，你需要创建一个 `nn.MSELoss()` 的实例。你可以通过传递一些参数来自定义其行为，但通常情况下，使用默认参数就足够了。
2. **准备数据**：准备你的输入数据和对应的目标（真实值）数据。这些数据应该是 PyTorch 张量（Tensor）。
3. **模型预测**：使用你的模型对数据进行预测，得到预测值。
4. **计算损失**：将预测值和目标值传递给 `nn.MSELoss()` 实例，以计算损失。
5. **反向传播和优化**（可选）：在训练过程中，你还需要进行反向传播来更新模型的参数。这通常涉及调用损失张量的 `.backward()` 方法来计算梯度，并使用优化器来更新参数。

实例：

```py
import torch  
import torch.nn as nn  
  
# 实例化 MSELoss  
loss_fn = nn.MSELoss()  
  
# 准备数据  
# 假设我们有一个简单的回归问题，输入是特征，目标是连续值  
inputs = torch.tensor([[1.0, 2.0, 3.0], [4.0, 5.0, 6.0]], requires_grad=False)  
targets = torch.tensor([[2.0], [5.0]], requires_grad=False)  # 注意 targets 的形状，它应该与预测值的形状相匹配  
  
# 假设我们有一个简单的线性模型  
model = nn.Linear(3, 1)  # 输入特征为3，输出特征为1（因为我们正在做回归）  
  
# 预测  
predictions = model(inputs)  
  
# 计算损失  
loss = loss_fn(predictions, targets)  
  
print(f"Loss: {loss.item()}")  
  
# 注意：在实际的训练循环中，你还需要进行反向传播和优化步骤  
# 这里只是展示了如何计算损失
```

### 16.6nn.CrossEntropyLoss()

`nn.CrossEntropyLoss()` 的主要作用是计算给定预测值（通常是经过 softmax 函数处理后的概率分布）和目标值（真实的类别标签）之间的交叉熵损失。这个损失函数内部会先对预测值应用 log_softmax 函数（如果你没有显式地应用 softmax），然后计算与目标值之间的交叉熵。

**使用**

使用 `nn.CrossEntropyLoss()` 时，你需要注意以下几点：

1. **预测值的维度**：预测值通常是模型输出层的原始分数（logits），其形状应该是 `[batch_size, num_classes]`，其中 `batch_size` 是批量大小，`num_classes` 是类别总数。
2. **目标值的维度**：目标值（真实标签）的形状应该是 `[batch_size]`，每个元素的值是对应样本的类别索引（从 0 到 `num_classes-1`）。
3. **不需要显式 softmax**：由于 `nn.CrossEntropyLoss()` 内部会应用 log_softmax，因此你不需要在传递给损失函数之前对预测值应用 softmax 函数。
4. **权重和忽略索引**（可选）：你还可以为不同的类别指定权重，或者指定某些样本或类别在计算损失时应该被忽略。

实例：

```py
import torch  
import torch.nn as nn  
  
# 实例化 CrossEntropyLoss  
loss_fn = nn.CrossEntropyLoss()  
  
# 准备数据  
# 假设我们有一个简单的分类问题，有 3 个类别  
logits = torch.tensor([[2.0, 1.0, 0.1],  # 第一个样本的预测分数  
                       [1.0, 0.2, 1.5]], # 第二个样本的预测分数  
                      requires_grad=True)  
targets = torch.tensor([0, 2])  # 真实标签，对应第一个样本属于类别 0，第二个样本属于类别 2  
  
# 计算损失  
loss = loss_fn(logits, targets)  
  
print(f"Loss: {loss.item()}")  
  
# 反向传播（仅作为示例，通常会在优化循环中进行）  
loss.backward()  
  
# 注意：在实际的训练循环中，你还需要进行参数更新（optimizer.step()）  
# 这里只是展示了如何计算损失和进行反向传播
```

### 16.7反向传播

1. `optim.zero_grad()`
   - 在进行反向传播之前，这一步是必须的。它用于清除（或归零）所有已存在的梯度信息。在PyTorch中，梯度是自动计算的，但在多次迭代中，梯度会累加。因此，在每次迭代开始时，需要清除旧的梯度，以避免梯度累积导致的错误。
2. `result_loss.backward()`
   - 这一行执行反向传播。它根据损失值 `result_loss` 计算模型中每个参数的梯度。这些梯度指明了如何调整模型参数以减小损失值。
3. `optim.step()`
   - 使用优化器 `optim` 根据计算出的梯度来更新模型的参数。这一步实际上是在“优化”模型，通过调整参数来减少损失值，从而提高模型的预测准确性。

## 17.优化器

Lr = learning rate 学习速率

优化器（Optimizer）在深度学习和神经网络训练过程中扮演着至关重要的角色。它的主要作用是调整（或优化）模型的参数，以最小化或最大化某个目标函数（通常是损失函数），从而改善模型在训练数据上的性能。

### 17.1 代码实现

```python
import torchvision
from torch import nn
import torch
from torch.nn import Conv2d
from torch.nn import MaxPool2d
from torch.nn import Flatten,Linear,Sequential
from torch.utils.data import DataLoader
dataset = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=False, download=True,transform=torchvision.transforms.ToTensor())
dataloader = DataLoader(dataset,batch_size=64)
class TUdui(nn.Module):
    def __init__(self):
        super(TUdui, self).__init__()
        self.module1 = Sequential(
            Conv2d(3, 32, kernel_size=5, padding=2),
            MaxPool2d(2),
            Conv2d(32, 32, kernel_size=5, padding=2),
            MaxPool2d(2),
            Conv2d(32, 64, kernel_size=5, padding=2),
            MaxPool2d(2),
            Flatten(),
            Linear(1024, 64),
            Linear(64, 10)
        )

    def forward(self, x):
        x = self.module1(x)
        return x
loss = nn.CrossEntropyLoss()
tudui = TUdui()
optim = torch.optim.SGD(tudui.parameters(), lr=0.01)
for epoch in range(20):
    running_loss = 0.0
    for data in dataloader:
        imgs, targets = data
        outputs = tudui(imgs)
        result_loss = loss(outputs, targets)
        optim.zero_grad()
        result_loss.backward()
        optim.step()
        running_loss = running_loss + result_loss
    print(running_loss)
```

### 17.2 优化器的步骤

1. **`optim.zero_grad()`**

   这个步骤是清除（或归零）所有已计算梯度的关键。在PyTorch中，梯度是自动累加的，这意味着如果你多次在同一个图上执行反向传播，梯度会被累加而不是覆盖。然而，在训练神经网络时，我们希望在每次迭代（或称为每个批次）开始时都有一个干净的梯度状态。因此，在调用`loss.backward()`之前，我们使用`optim.zero_grad()`来确保梯度被清零。

   注意，这里的`optim`是一个优化器对象，它封装了用于更新网络参数的算法（如SGD、Adam等）。然而，`zero_grad()`方法并不直接作用于参数，而是作用于与这些参数相关联的梯度。

2. **`result_loss.backward()`**

   这个步骤执行反向传播算法。`result_loss`是损失函数的输出，它衡量了当前批次数据的模型预测与真实标签之间的差异。通过调用`result_loss.backward()`，PyTorch会自动计算图中所有可训练参数（即那些`requires_grad=True`的参数）的梯度。这些梯度存储在参数的`.grad`属性中，并用于后续的参数更新。

   注意，`backward()`方法需要在计算图（graph）中调用，该图包含了从输入到损失的所有操作。在PyTorch中，这个图是通过动态图机制隐式构建的，它允许我们在运行时构建和修改图。

3. **`optim.step()`**

   这个步骤使用优化器来更新网络的参数。在调用`optim.step()`之前，必须确保已经调用了`optim.zero_grad()`和`loss.backward()`（或类似地，`result_loss.backward()`），因为`step()`方法会使用存储在参数`.grad`属性中的梯度来更新参数。

   `optim.step()`执行了具体的更新规则，这取决于优化器的类型（如SGD、Adam等）。在大多数情况下，这个步骤会遍历优化器管理的所有参数，并根据它们各自的梯度来更新它们的值。

### 17.3 torch.optim.SGD()

`torch.optim.SGD()` 是 PyTorch 中实现随机梯度下降（Stochastic Gradient Descent, SGD）优化算法的一个类。随机梯度下降是一种广泛使用的优化算法，用于训练深度学习模型，它通过迭代地更新网络参数来最小化损失函数。在每次迭代中，SGD 算法会根据当前小批量（mini-batch）数据的梯度来更新模型参数。

形式：

```py
torch.optim.SGD(params, lr=required, momentum=0, dampening=0, weight_decay=0, nesterov=False, *, maximize=False)
```

- **params** (iterable): 需要优化的参数的迭代器（通常是模型中的 `parameters()`）。
- **lr** (float): 学习率，用于控制参数更新的步长。这是必需的参数。
- **momentum** (float, 可选): 动量因子，用于加速 SGD 在相关方向上的更新，并抑制震荡。默认为 0。
- **dampening** (float, 可选): 用于动量计算的阻尼项，以改进在某些情况下的收敛性。默认为 0。
- **weight_decay** (float, 可选): 权重衰减（L2惩罚），这有助于防止过拟合。默认为 0。
- **nesterov** (bool, 可选): 启用 Nesterov 动量。默认为 False。当设置为 True 时，它使用 Nesterov 的动量变种，这通常可以比标准的动量更快地收敛。
- **maximize** (bool, 可选): 当设置为 True 时，优化器会尝试最大化函数（例如，在 GANs 中训练判别器时）。默认为 False。

## 18.现有网络模型的使用及修改

 

### 18.1 对网络模型进行添加和修改的代码实现

```python
import torchvision
from torch import nn

#train_data = torchvision.datasets.ImageNet("C:\\pythonProject3\\pytorch\\dataset",split='train',download=True
#                                           ,transform=torchvision.transforms.ToTensor())
vgg16_false = torchvision.models.vgg16(pretrained=False)
vgg16_true = torchvision.models.vgg16(pretrained=True)
print(vgg16_true)
train_data = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=True, download=True,transform=torchvision.transforms.ToTensor())
vgg16_true.classifier.add_module('add_linear',nn.Linear(1000, 10))
print(vgg16_true)

print(vgg16_false)
vgg16_false.classifier[6] = nn.Linear(4096, 10)
print(vgg16_false)
```

### 18.2 torchvision.models

`torchvision.models` 是 PyTorch 中的一个非常有用的模块，它提供了一系列预训练的模型，这些模型可以在各种图像识别任务中直接使用或进行微调。这些模型通常包括在大型数据集（如 ImageNet）上预训练的经典网络架构，如 AlexNet, VGG, ResNet, Inception, DenseNet, MobileNet, ShuffleNet 等。

**作用**

1. **快速启动项目**：对于许多图像识别任务，你可以直接使用这些预训练模型作为起点，而无需从头开始训练模型。
2. **特征提取**：预训练模型可以作为特征提取器，用于提取图像的高级特征，这些特征可以进一步用于其他任务，如图像分类、图像检索、图像标注等。
3. **迁移学习**：通过微调预训练模型的最后一层或几层，可以使其适应新的数据集和任务，这种方法称为迁移学习，可以显著提高模型的训练效率和性能。

## 19.网络模型的保存与读取

### 19.1 model_save

```python
import torchvision
import torch
import torch.nn as nn

vgg16 = torchvision.models.vgg16(pretrained=False)
#保存方式1 模型结构+模型参数
torch.save(vgg16,'vgg16.pth')
#保存方式2 模型参数(官方推荐)
torch.save(vgg16.state_dict(),'vgg16_state_dict.pth')
#陷阱1
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.conv1 = nn.Conv2d(3, 64,3)

    def forward(self, x):
        x = self.conv1(x)
        return x

tudui = Tudui()
torch.save(tudui,'tudui.pth')
```

### 19.2 model_load

```python
import torch
import torchvision
import torch.nn as nn
#方式1 -> 保存方式1，加载模型
model = torch.load("C:\\pythonProject3\\pytorch\\vgg16.pth")
print(model)
#方式2，加载模型
vgg16 = torchvision.models.vgg16(pretrained=False)
vgg16.load_state_dict(torch.load("C:\\pythonProject3\\pytorch\\vgg16_state_dict.pth"))
#model = torch.load("C:\\pythonProject3\\pytorch\\vgg16_state_dict.pth")
#print(model)
print(vgg16)
#陷阱1
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.conv1 = nn.Conv2d(3, 64,3)

    def forward(self, x):
        x = self.conv1(x)
        return x
model = torch.load("C:\\pythonProject3\\pytorch\\tudui.pth")
print(model)
```

## 20.完整的模型训练套路

![image-20240813154014214](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240813154014214.png)

### 20.1 train.py

```py
import torchvision
from torch import nn
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter

from model import *

# 准备数据集
train_data = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=True, download=True,transform=torchvision.transforms.ToTensor())

test_data = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=False, download=True,transform=torchvision.transforms.ToTensor())

# length 长度
train_data_size = len(train_data)
test_data_size = len(test_data)
print("Train data size: {}".format(train_data_size))
print("Test data size: {}".format(test_data_size))

# 利用 DataLoader 来加载数据集
train_dataloader = DataLoader(train_data, batch_size=64)
test_dataloader = DataLoader(test_data, batch_size=64)

# 搭建神经网络
tudui = Tudui()

# 损失函数
loss_fn = nn.CrossEntropyLoss()

#优化器
optimizer = torch.optim.SGD(tudui.parameters(), lr=0.01)

# 设置训练网络的一些参数
# 记录训练的次数
total_train_step = 0
# 记录测试的次数
total_test_step = 0
# 训练的论数
epoch = 10

# 追加tensorboard
writer = SummaryWriter("C:\\pythonProject3\\pytorch\\logs_train")

for i in range(epoch):
    print("Epoch {}".format(i+1))

    # 训练步骤开始
    tudui.train()
    for data in train_dataloader:
        imgs,targets = data
        outputs = tudui(imgs)
        loss = loss_fn(outputs, targets)
        #优化器优化模型
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
        total_train_step += 1
        if total_train_step % 100 == 0:
            print("Loss: {}".format(loss.item()))
            writer.add_scalar("train_loss", loss.item(), total_train_step)

    #测试步骤开始
    tudui.eval()
    total_test_loss = 0
    total_accuracy = 0
    with torch.no_grad():
        for data in test_dataloader:
            imgs,targets = data
            outputs = tudui(imgs)
            loss = loss_fn(outputs, targets)
            total_test_loss += loss.item()
            accuracy = (outputs.argmax(1) == targets).sum()
            total_accuracy = total_accuracy + accuracy
    print("Test Loss: {}".format(total_test_loss))
    print("total_accuracy: {}".format(total_accuracy/train_data_size))
    writer.add_scalar("test_loss", total_test_loss, total_test_step)
    writer.add_scalar("test_accuracy", total_accuracy/train_data_size, total_test_step)
    total_test_step += 1

    torch.save(tudui, 'tudui_{}.pth'.format(i))
    print("模型已保存")
writer.close()
```

### 20.2 model.py

```py
import torchvision
from torch import nn
import torch
from torch.utils.data import DataLoader
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.model = nn.Sequential(
            nn.Conv2d(3, 32,5, 1,2),
            nn.MaxPool2d(2),
            nn.Conv2d(32, 32,5,1, 2),
            nn.MaxPool2d(2),
            nn.Conv2d(32,64,5,1,2),
            nn.MaxPool2d(2),
            nn.Flatten(),
            nn.Linear(64*4*4,64),
            nn.Linear(64,10)
        )
    def forward(self, x):
        x = self.model(x)
        return x

if __name__ == '__main__':
    tudui = Tudui()
    input = torch.ones(64,3,32,32)
    output = tudui(input)
    print(output.shape)
```

## 21.利用GPU训练

### 21.1 能使用cuda的对象

1.网络模型

2.数据(输入，标注)

3.损失函数

### 21.2 用.cuda()进行GPU训练

```py
import torchvision
import torch
from torch import nn
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter
import time
#from model import *

# 准备数据集
train_data = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=True, download=True,transform=torchvision.transforms.ToTensor())

test_data = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=False, download=True,transform=torchvision.transforms.ToTensor())
# length 长度
train_data_size = len(train_data)
test_data_size = len(test_data)
print("Train data size: {}".format(train_data_size))
print("Test data size: {}".format(test_data_size))

# 利用 DataLoader 来加载数据集
train_dataloader = DataLoader(train_data, batch_size=64)
test_dataloader = DataLoader(test_data, batch_size=64)

# 搭建神经网络
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.model = nn.Sequential(
            nn.Conv2d(3, 32,5, 1,2),
            nn.MaxPool2d(2),
            nn.Conv2d(32, 32,5,1, 2),
            nn.MaxPool2d(2),
            nn.Conv2d(32,64,5,1,2),
            nn.MaxPool2d(2),
            nn.Flatten(),
            nn.Linear(64*4*4,64),
            nn.Linear(64,10)
        )
    def forward(self, x):
        x = self.model(x)
        return x
tudui = Tudui()
if torch.cuda.is_available():
    tudui = tudui.cuda()

# 损失函数
loss_fn = nn.CrossEntropyLoss()
if torch.cuda.is_available():
    loss_fn = loss_fn.cuda()
#优化器
optimizer = torch.optim.SGD(tudui.parameters(), lr=0.01)

# 设置训练网络的一些参数
# 记录训练的次数
total_train_step = 0
# 记录测试的次数
total_test_step = 0
# 训练的论数
epoch = 10

# 追加tensorboard
writer = SummaryWriter("C:\\pythonProject3\\pytorch\\logs_train")
start_time = time.time()
for i in range(epoch):
    print("Epoch {}".format(i+1))

    # 训练步骤开始
    tudui.train()
    for data in train_dataloader:
        imgs,targets = data
        if torch.cuda.is_available():
            imgs = imgs.cuda()
            targets = targets.cuda()
        outputs = tudui(imgs)
        loss = loss_fn(outputs, targets)
        #优化器优化模型
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
        total_train_step += 1
        if total_train_step % 100 == 0:
            end_time = time.time()
            print(end_time - start_time)
            print("Loss: {}".format(loss.item()))
            writer.add_scalar("train_loss", loss.item(), total_train_step)

    #测试步骤开始
    tudui.eval()
    total_test_loss = 0
    total_accuracy = 0
    with torch.no_grad():
        for data in test_dataloader:
            imgs,targets = data
            if torch.cuda.is_available():
                imgs = imgs.cuda()
                targets = targets.cuda()
            outputs = tudui(imgs)
            loss = loss_fn(outputs, targets)
            total_test_loss += loss.item()
            accuracy = (outputs.argmax(1) == targets).sum()
            total_accuracy = total_accuracy + accuracy
    print("Test Loss: {}".format(total_test_loss))
    print("total_accuracy: {}".format(total_accuracy/train_data_size))
    writer.add_scalar("test_loss", total_test_loss, total_test_step)
    writer.add_scalar("test_accuracy", total_accuracy/train_data_size, total_test_step)
    total_test_step += 1

    torch.save(tudui, 'tudui_{}.pth'.format(i))
    print("模型已保存")
writer.close()
```

### 21.3 用.to(device)进行GPU训练

eg:

```py
.to(device)
Device = torch.device("cpu")
Torch.device("cuda")
TOrch.device("cuda:0")
Torch.device("cuda:1")
```

代码实现：

```py
import torchvision
import torch
from torch import nn
from torch.utils.data import DataLoader
from torch.utils.tensorboard import SummaryWriter
import time
#from model import *
#定义训练的设备
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
# 准备数据集
train_data = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=True, download=True,transform=torchvision.transforms.ToTensor())

test_data = torchvision.datasets.CIFAR10(root='C:\\pythonProject3\\pytorch\\dataset', train=False, download=True,transform=torchvision.transforms.ToTensor())
# length 长度
train_data_size = len(train_data)
test_data_size = len(test_data)
print("Train data size: {}".format(train_data_size))
print("Test data size: {}".format(test_data_size))

# 利用 DataLoader 来加载数据集
train_dataloader = DataLoader(train_data, batch_size=64)
test_dataloader = DataLoader(test_data, batch_size=64)

# 搭建神经网络
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.model = nn.Sequential(
            nn.Conv2d(3, 32,5, 1,2),
            nn.MaxPool2d(2),
            nn.Conv2d(32, 32,5,1, 2),
            nn.MaxPool2d(2),
            nn.Conv2d(32,64,5,1,2),
            nn.MaxPool2d(2),
            nn.Flatten(),
            nn.Linear(64*4*4,64),
            nn.Linear(64,10)
        )
    def forward(self, x):
        x = self.model(x)
        return x
tudui = Tudui()
tudui.to(device)

# 损失函数
loss_fn = nn.CrossEntropyLoss()
loss_fn = loss_fn.to(device)
#优化器
optimizer = torch.optim.SGD(tudui.parameters(), lr=0.01)

# 设置训练网络的一些参数
# 记录训练的次数
total_train_step = 0
# 记录测试的次数
total_test_step = 0
# 训练的论数
epoch = 10

# 追加tensorboard
writer = SummaryWriter("C:\\pythonProject3\\pytorch\\logs_train")
start_time = time.time()
for i in range(epoch):
    print("Epoch {}".format(i+1))

    # 训练步骤开始
    tudui.train()
    for data in train_dataloader:
        imgs,targets = data
        imgs = imgs.to(device)
        targets = targets.to(device)
        outputs = tudui(imgs)
        loss = loss_fn(outputs, targets)
        #优化器优化模型
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
        total_train_step += 1
        if total_train_step % 100 == 0:
            end_time = time.time()
            print(end_time - start_time)
            print("Loss: {}".format(loss.item()))
            writer.add_scalar("train_loss", loss.item(), total_train_step)

    #测试步骤开始
    tudui.eval()
    total_test_loss = 0
    total_accuracy = 0
    with torch.no_grad():
        for data in test_dataloader:
            imgs,targets = data
            imgs = imgs.to(device)
            targets = targets.to(device) 
            outputs = tudui(imgs)
            loss = loss_fn(outputs, targets)
            total_test_loss += loss.item()
            accuracy = (outputs.argmax(1) == targets).sum()
            total_accuracy = total_accuracy + accuracy
    print("Test Loss: {}".format(total_test_loss))
    print("total_accuracy: {}".format(total_accuracy/train_data_size))
    writer.add_scalar("test_loss", total_test_loss, total_test_step)
    writer.add_scalar("test_accuracy", total_accuracy/train_data_size, total_test_step)
    total_test_step += 1

    torch.save(tudui, 'tudui_{}.pth'.format(i))
    print("模型已保存")
writer.close()
```

## 22.完整的模型验证套路

套路：利用已经训练好的模型，然后给它提供输入

```py
from PIL import Image
import torchvision
from torch import nn
import torch
image_path = "C:\\pythonProject3\\pytorch\\R-C.jpg"
image = Image.open(image_path).convert('RGB')
print(image)
transform = torchvision.transforms.Compose([torchvision.transforms.Resize((32, 32)), torchvision.transforms.ToTensor()])
image = transform(image)
print(image.shape)
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
class Tudui(nn.Module):
    def __init__(self):
        super(Tudui, self).__init__()
        self.model = nn.Sequential(
            nn.Conv2d(3, 32,5, 1,2),
            nn.MaxPool2d(2),
            nn.Conv2d(32, 32,5,1, 2),
            nn.MaxPool2d(2),
            nn.Conv2d(32,64,5,1,2),
            nn.MaxPool2d(2),
            nn.Flatten(),
            nn.Linear(64*4*4,64),
            nn.Linear(64,10)
        )
    def forward(self, x):
        x = self.model(x)
        return x
model = torch.load("tudui_9.pth")
print(model)
model = Tudui().to(device)
image = torch.reshape(image,(1,3,32,32))
image = image.to(device)
model.eval()
with torch.no_grad():
    output = model(image)
print(output)
```


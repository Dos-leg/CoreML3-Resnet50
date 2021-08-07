# CoreML3-Resnet50

介绍
想象一下，在不需要深入了解机器学习的情况下，使用最先进的机器学习模型来构建应用程序。这就是Apple的Core ML 3!
你是Apple的狂热粉丝吗?你用iPhone吗?有没有想过Apple是如何利用机器学习和深度学习来驱动其应用和软件的?
如果你对以上任何一个问题的回答是肯定的，那么你将会得到一场盛宴!因为在本文中，我们将使用深度学习和Apple的Core ML 3为iPhone构建一个应用程序。下面是这款应用的快速浏览:

软件开发人员、程序员甚至数据科学家都喜欢Apple的人工智能生态。近年来，他们取得了一些惊人的进展，包括Core ML和我个人最喜欢的Swift编程语言。
Core ML 3是一个框架，支持iPhone的一些功能，比如FaceID、Animoji和增强现实AR。自从Core ML在2017年发布以来，它已经走过了很长的路，现在它支持大量的工具，可以帮助我们快速构建基于机器学习的应用程序。
在这篇文章中，我们将探索Apple应用程序的整个人工智能生态，以及如何使用Core ML 3丰富的生态，包括前沿的预训练深度模型。
目录
Apple的人工智能生态
Core ML 3
Core ML 3的新特性
使用ResNet50为iPhone构建一个图像分类应用
分析Vidhya对Core ML的看法
Apple的人工智能生态
Apple在构建利用机器学习的工具和框架方面做得很好。构建人工智能应用程序有多种选择，每种选择都有其优缺点。

让我们了解一下每个工具或框架。
1)Turi Create
这应该是你的首选框架，如果你想添加推荐，对象检测，图像分类，图像相似性或活动分类等任务到你的应用程序。
使用这个工具你不需要成为机器学习专家因为它已经为每个任务定义了模型。
我喜欢Turi Create的一点是，我们可以在Python中使用它，就像我们的常规工作流程一样。当我们对我们的模型感到满意时，只需将它导入到Core ML中，就可以在iOS、macOS、watchOS和tvOS应用程序中使用!
以下是Turi Create的支持的一些任务:

2)CreateML
Create ML使我们能够构建机器学习模型，而不需要编写太多代码。
我喜欢这个工具的地方是，你可以拖放你的训练数据，选择你想要的模型类型(语音识别，对象检测等)，它会自动开始训练模型!
下面是一个训练猫狗图像分类器的例子:

请注意，我只编写了两行代码并拖拽训练数据到目标文件夹，其余部分都由CreateML负责!
Turi Create可以在Python中工作，而我们可以使用CreateML在Mac上构建程序。并且它支持在GPU上进行训练
3)用于TensorFlow的Swift
Swift for TensorFlow有一个灵活、高性能的类似于TensorFlow/PyTorch的API来构建复杂的神经网络架构。
这个框架最吸引人的地方是它的代码和Python的代码一样易读。以下是相同的模型在Swift和Python的不同表达(注意相似性):

当你需要模型的高性能并希望有效地部署它们时，可以选择Swift来使用TensorFlow。
4)语言和视觉框架
这些是Apple针对Python的spaCy和OpenCV框架创建的副本，但是增加了功能。这些框架允许我们创建端到端管道来执行图像处理和文本处理等。
如果你想执行图像分析任务，如人脸或地标检测、文本检测、条形码识别、图像配准和一般特征跟踪，那么视觉就是你的选择。

类似地，如果你想执行诸如语言和脚本识别、分词、lemmatization、词性分析和命名实体识别等任务，那么语言模块将会很有用。

除了这两个，Apple还支持处理语音数据的框架(并且它们很容易与CoreML一起工作)。我将在以后的文章中介绍这些工具。现在，让我们来看看最精彩的框架——ML 3!
Core ML 3
我喜欢Apple的Core ML 3框架。它不仅支持我们在上面看到的工具，而且还支持它自己的一些功能。
首先，CoreML3允许我们导入主流的Python框架中训练过的机器学习或深度学习模型:

我们在前面的一篇文章中已经介绍了Core ML 3的这个功能。在这里，我们将看到CoreML3的另一个有趣的功能，我们如何利用CoreML3使用大量前沿的预训练模型!
下面是Core ML 3支持的模型列表。注意其中的一些(比如Squeezenet, DeeplabV3, YOLOv3)是最近几个月才出现的:

所有这些模型实际上都经过了优化，以便在移动设备、平板电脑和电脑上提供最佳性能。这就是Apple的伟大之处。
这意味着，即使其中许多是复杂的基于深度学习的模型，我们也不必在部署和在应用程序中使用它们时过多地担心性能——这有多酷?
Core ML 3的新特性
你看了今年的WWDC大会了吗?关于Apple设备对这个框架的支持，有一些有趣的公告。这里有一个简短的总结，以防你错过。
1)设备内置的训练
这是Core ML 3目前为止最突出的功能。之前，我们只支持“设备上的推理”。这基本上意味着我们在其他机器上训练我们的模型，然后利用训练好的模型对设备本身进行实时预测。新功能导致了更好的用户体验，因为我们不依赖互联网来获得预测。
Core ML 3现在也支持设备上的训练!你可以使用iPhone的CPU、GPU和神经引擎来训练你的机器学习和深度学习模型。
你可以将Core ML 3训练视为一种迁移学习或在线学习的形式，在这种形式中，你只需要调整现有的模型。
以Face ID为例。当用户的脸随着时间变化(长胡子、化妆、变老等)时，它需要保持模型的更新。基本思想是，首先拥有一个通用模型，它为每个人提供平均性能，然后为每个用户定制一个副本。
随着时间的推移，这个模型会变得非常适合特定的用户:

这样做有很多好处:
训练将在用户的个人设备上进行，这对用户来说意味着很高的数据隐私
我们不需要设置庞大的服务器来帮助数百万应用程序用户进行模型训练
因为不涉及互联网，这些模型预测时一直可用!
2)在Core ML 3中加入了新型的神经网络层

除了为不同的模型类型提供层外，Core ML 3还为中间操作提供了100多个层，比如掩蔽、张量操作、布尔逻辑、控制流等等。
这些层类型中的一些已经被用在最先进的神经网络架构中，Core ML 3已经为我们提供了支持。
这仅仅意味着我们可以很容易地为我们的应用程序立即构建这样的模型。
如果你对整个包感兴趣，可以免费观看整个WWDC视频。出于本文的目的，我们介绍了core ML 3的核心基础知识。现在是时候构建一个iPhone应用程序了!视频链接：https://developer.apple.com/videos/play/wwdc2019/704/
为iPhone建立一个图像分类应用
在我们开始构建应用程序之前，我们需要安装一些东西。
系统设置
macOS:我用的是macOS Catalina (10.15.1)
Xcode:这是为Apple设备开发应用的默认软件。你可以从Apple电脑上的App Store下载。我用的是11.2版
Project:你可以在你的终端使用下面的命令从GitHub下载项目的基本代码:
git clone https://github.com/mohdsanadzakirizvi/CoreML3-Resnet50.git注意:
对于本文，你需要一台macOS机器，否则无法实现该项目
任何为Apple设备开发的应用程序都是用Swift编写的
建立我们的深度学习模型
一旦你下载项目，你会看到有两个文件夹:

图片上的完整版是应用程序的全功能版本，你可以通过导入ResNet50模型来运行。练习版缺少一些代码。
在Xcode中运行以下命令打开项目:
open ImageClassifier.xcodeproj

我在Xcode窗口中突出显示了三个主要区域:
左上角的play按钮用于在模拟器上start the app
如果你看下面的play按钮，有文件和文件夹的项目。这称为项目导航器。它帮助我们在项目的文件和文件夹之间导航
在播放按钮旁边写着iPhone 11 Pro Max。这表示要测试模拟器的目标设备
让我们先运行我们的应用程序，看看会发生什么。点击左上角的播放按钮，模拟器就会运行。你看到了什么?

目前，我们的应用程序还做不了什么。它只显示一个图像和一个按钮来选择其他图像-让我们做得更好!
如果你打开Pratice版本，你会发现以下文件夹结构:

在项目导航窗格中，选择ViewController.swift。这个文件包含了很多控制我们应用程序功能的代码。
import CoreMLimport Visionimport UIKitclass ViewController: UIViewController { @IBOutlet weak var scene: UIImageView! @IBOutlet weak var answerLabel: UILabel! override func viewDidLoad() { super.viewDidLoad() guard let image = UIImage(named: "scenery") else { fatalError("no starting image") } scene.image = image }}extension ViewController { @IBAction func pickImage(_ sender: Any) { let pickerController = UIImagePickerController() pickerController.delegate = self pickerController.sourceType = .savedPhotosAlbum present(pickerController, animated: true) }}// UIImagePickerControllerDelegateextension ViewController: UIImagePickerControllerDelegate { func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [String : Any]) { dismiss(animated: true) guard let image = info[UIImagePickerControllerOriginalImage] as? UIImage else { fatalError("couldn't load image from Photos") } scene.image = image }}//UINavigationControllerDelegateextension ViewController: UINavigationControllerDelegate {}现在你已经熟悉了Xcode和项目代码文件，让我们进入下一个阶段。
在我们的应用程序中添加一个预训练模型
前往官方Core ML 3网站直接下载预训练的模型:
https://developer.apple.com/machine-learning/models/在image部分，你可以找到ResNet50:

你可以下载任何你想要的版本。尺寸越大，模型就越精确。同样，尺寸越小，模型运行的速度越快。
拖拽Resnet50.mlmodel文件放入项目导航窗格中的文件夹
将弹出一个带有一些选项的窗口。选择默认选项，然后点击“Finish”
当我们将这样的文件拖放到Xcode中时，它会自动创建对该文件的引用。通过这种方式，我们可以轻松地在代码中访问该文件
以下是整个流程供参考:

做出第一个预测
为了进行第一次预测，我们需要加载刚刚下载的ResNet50模型。然后，取一幅图像，将它转换成模型期望的格式并进行预测。
在ViewController.swift文件的IBActions(第33行)下面编写以下代码:
extension ViewController { func imageClassify(image: CIImage) { answerLabel.text = "detecting..." // 通过生成的类加载ML模型 guard let model = try? VNCoreMLModel(for: Resnet50().model) else { fatalError("can't load Places ML model") } // 创建带有处理程序的视觉请求 let request = VNCoreMLRequest(model: model) { [weak self] request, error in let results = request.results as? [VNClassificationObservation] var outputText = "" for res in results!{ outputText += "\(Int(res.confidence * 100))% it's \(res.identifier)\n" } DispatchQueue.main.async { [weak self] in self?.answerLabel.text! = outputText } } // 在全局调度队列上运行CoreML3 Resnet50分类器 let handler = VNImageRequestHandler(ciImage: image) DispatchQueue.global(qos: .userInteractive).async { do { try handler.perform([request]) } catch { print(error) } } }}上面的代码接收一个新图像，根据ResNet50期望的格式对其进行预处理，然后将其传递到网络中进行预测。
最重要的代码行是:
// 通过生成的类加载ML模型guard let model = try? VNCoreMLModel(for: Resnet50().model) else {fatalError("can't load Places ML model")}我们在这里设置模型名称。如果你想使用像BERT或YOLO这样的框架，你只需要修改模型名，你的应用程序的其他部分就可以顺利运行了。
现在，我们需要调用这个函数imageClassify()来获得对图像的预测。将下面这段代码添加到viewDidLoad()的末尾(第19行):
guard let ciImage = CIImage(image: image) else { fatalError("couldn't convert UIImage to CIImage") } classifyImage(image: ciImage)现在，如果你运行这个应用程序，你会看到它已经开始预测当应用程序启动时显示的风景图片:

在imagePickerController()中复制相同的代码(第87行)，然后应用程序将能够对你选择的任何图像做出相同的预测。
这是应用程序的最终版本:

恭喜你——你刚刚为iPhone开发了第一款人工智能应用!
Vidhya对Core ML 3的分析
Apple公司利用最新的人工智能图像、语音和文本研究，开发出令人印象深刻的应用程序。你可以立即开始，而不必对这些模型有太多的了解，并在此过程中学习和探索。
我喜欢这个行业认真对待人工智能的方式，这让更广泛的受众能够接触到它。
我鼓励你进一步探索和尝试最新的模型，如BERT，并创建更有趣的应用程序。如果想选择其他模型的话，你可以尝试在我们这里开发的同一个应用程序上使用SqueezeNet和MobileNet，看看不同的模型是如何在相同的图像上运行的。


# License
MIT

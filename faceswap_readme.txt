根据【faceswap.py [-h]】命令导出后翻译。

参数内容: {extract,train,convert,gui}
    extract           从图片中提取面部特征
    train             训练一个模型，用于识别A和B两张脸。
    convert           使用训练的模型，置换原图片的脸到新的面部。
    gui               加载图形界面运行faceswap


【faceswap.py extract】从图片中提取脸部特征
usage: faceswap.py extract [-h] [-L {INFO,VERBOSE,DEBUG,TRACE}] [-LF LOGFILE]
                           [-i INPUT_DIR] [-o OUTPUT_DIR]                
                           [-al ALIGNMENTS_PATH] [-l REF_THRESHOLD]
                           [-n NFILTER [NFILTER ...]] [-f FILTER [FILTER ...]]
                           [--serializer {json,pickle,yaml}]
                           [-D {dlib-cnn,dlib-hog,mtcnn}] [-A {dlib,fan}]
                           [-mtms MTCNN_MINSIZE]
                           [-mtth MTCNN_THRESHOLD [MTCNN_THRESHOLD ...]]
                           [-mtsc MTCNN_SCALEFACTOR] [-r ROTATE_IMAGES]
                           [-bt BLUR_THRESH] [-mp] [-sz SIZE] [-s] [-sf] [-dl]
                           [-ae] [-si SAVE_INTERVAL]

optional arguments:
  -h, --help           
            显示本帮助信息然后退出
  -L {INFO,VERBOSE,DEBUG,TRACE}, --loglevel {INFO,VERBOSE,DEBUG,TRACE}
            配置日志级别。除非你需要提交故障报告，否则请坚持用INFO或VERBOSE来提供信息或详细信息。
            在使用TRACE参数时特别注意，因为它会产生很多的数据。

  -LF LOGFILE, --logfile LOGFILE           
            存储日志文件的路径。参数留空保存在FACESWAP文件夹。
                     
  -i INPUT_DIR, --input-dir INPUT_DIR
            输入目录或视频。目录包含要处理的图像文件或路径到视频文件。默认为“input”。
                       
  -o OUTPUT_DIR, --output-dir OUTPUT_DIR
            输出目录。这是转换文件的位置将被存储。默认为“output”。
                       
  -al ALIGNMENTS_PATH, --alignments ALIGNMENTS_PATH
            参数文件的路径配置。
                      
  -l REF_THRESHOLD, --ref_threshold REF_THRESHOLD
            面部识别阈值。
                        
  -n NFILTER [NFILTER ...], --nfilter NFILTER [NFILTER ...]
            配置不想被特征提取的图片过滤器。要求是正面的图像。多张图片可用空格分割。

  -f FILTER [FILTER ...], --filter FILTER [FILTER ...]
            配置指定的过滤器用于图片特征提取，要求是正面图像，多张图片可用空格分割。 

  --serializer {json,pickle,yaml}
            配置文件的序列格式，如果yaml格式被选择而且没有激活，那么json格式将在回传中被使用。
   
  -D {dlib-cnn,dlib-hog,mtcnn}, --detector {dlib-cnn,dlib-hog,mtcnn}
            要使用的探测器类型。              
                “dlib hog”：使用最少的资源，但最不可靠的。
                “dlib cnn”：比mtcnn快，但检测到更少的面孔和更少的假阳性。
                “mtcnn”：比dlib慢，但使用较少资源，同时检测更多人脸和更多误报。有优势看齐DLIB。

  -A {dlib,fan}, --aligner {dlib,fan}
           提取配置选择。
                "dlib"：dlib姿态检测。迅速、更少的资源占用，但不准确。
                "fan"：面向网络，需最佳曝光，但GPU资源占有大。  

  -mtms MTCNN_MINSIZE, --mtcnn-minsize MTCNN_MINSIZE
           面部识别的最小像素值。低值将耗费更多的内存。最低值为10，默认为20。

  -mtth MTCNN_THRESHOLD [MTCNN_THRESHOLD ...], --mtcnn-threshold MTCNN_THRESHOLD [MTCNN_THRESHOLD ...]
           面部检测的三级阈值。每一步值都需要少于1 。比如'--mtcnn-threshold 0.6 0.7 0.7'.
                  第一步：检测显然可见的面部
                  第二步：提纯面部特征值
                  第三步：进一步细化面部候选
                  默认值为 0.6 0.7 0.7

  -mtsc MTCNN_SCALEFACTOR, --mtcnn-scalefactor MTCNN_SCALEFACTOR
            图像渐增后配置的比例因数。应该是小于1的十进制数。默认值为0.709（仅在使用MTCNN时生效）

  -r ROTATE_IMAGES, --rotate-images ROTATE_IMAGES
            可旋转图像找脸。如果找不到人脸，请旋转图像以尝试检测。
            这个功能可以找到更多的面孔，但以牺牲提取速度为代价。
            使用前需要配置一个数字。该数字最大值为360。或通过列表可以精确枚举要检查的角度值。
 
 -bt BLUR_THRESH, --blur-threshold BLUR_THRESH
            设置模糊临界值用于检测时弃用照片。丢弃的图像将移动到名为“blurry”的子文件夹。设置的值越小，允许的模糊度越大。
                  
  -mp, --multiprocess   
             多线程提取配置。可以在一些提取检测时增速。只有在启用GPU的时候产生效果，否则都是自动的。

  -sz SIZE, --size SIZE
             输出的面部大小。确保您打算培训的模型，支持您所需的尺寸。这个更改更多地用于高分辨率模型。

  -s, --skip-existing  
             跳过在配置文件中已经存在的提取帧。

  -sf, --skip-existing-faces
             跳过在配置文件中已经存在的面部帧。

  -dl, --debug-landmarks
             在输出面上绘制标志以进行调试
  
  -ae, --align-eyes     
             进行额外校准以确保左眼/右眼等高

  -si SAVE_INTERVAL, --save-interval SAVE_INTERVAL
            设置配置文件自动保存间隔。
            当一组帧被读取后会自动保存在配置文件中。默认是在最后才保存。
            警告：不要再写入文件的时候中断脚本因为可能会带来损坏。
                       
【faceswap.py  train】训练一个模型，用于识别A和B两张脸
usage: faceswap.py train [-h] [-L {INFO,VERBOSE,DEBUG,TRACE}] [-LF LOGFILE]
                         [-A INPUT_A] [-B INPUT_B] [-m MODEL_DIR]
                         [-s SAVE_INTERVAL]
                         [-t {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}]
                         [-bs BATCH_SIZE] [-it ITERATIONS] [-g GPUS] [-p] [-w]
                         [-pl] [-ag] [-tia TIMELAPSE_INPUT_A]
                         [-tib TIMELAPSE_INPUT_B] [-to TIMELAPSE_OUTPUT]

参数内容:
  -h, --help            
                        显示帮助的信息，然后返回。
  -L {INFO,VERBOSE,DEBUG,TRACE}, --loglevel {INFO,VERBOSE,DEBUG,TRACE}
                        配置日志级别。除非你需要提交故障报告，否则请坚持用INFO或VERBOSE来提供信息或详细信息。
                        在使用TRACE参数时特别注意，因为它会产生很多的数据。

  -LF LOGFILE, --logfile LOGFILE
                        配置日志文件路径。留空的话，会在faceswap文件夹中生成日志。

  -A INPUT_A, --input-A INPUT_A
                       配置A脸的输入目录。需要提供含有A脸的训练图片的目录，用来训练A脸。默认需要输入。

  -B INPUT_B, --input-B INPUT_B
                       配置B脸的输入目录。需要提供含有A脸的训练图片的目录，用来训练A脸。默认需要输入。

  -m MODEL_DIR, --model-dir MODEL_DIR
                       配置训练模型的生成目录。这个模型会产生训练数据。默认需要输入。 

  -s SAVE_INTERVAL, --save-interval SAVE_INTERVAL
                       配置需要保存的模型迭代值。

  -t {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}, --trainer {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}
                       选择训练模式，使用LowMem模式进行训练的话，需要的显卡内存大于2GB。

  -bs BATCH_SIZE, --batch-size BATCH_SIZE
                        批处理尺寸,需要时2的整数倍，类似(64, 128, 256, 等等)

  -it ITERATIONS, --iterations ITERATIONS
                        重复训练的次数

  -g GPUS, --gpus GPUS  
                        配置多少GPU的数量用于训练

  -p, --preview        
                        显示输出预览，如果没有配置，就将进程写入文件。 

  -w, --write-image     
                        即使在预览模式，也要将训练结果写入到文件中

  -pl, --use-perceptual-loss
                       使用无感模式进行训练

  -ag, --allow-growth   
                       配置自增长的Tensorflow可以耗费多少备用内存

  -tia TIMELAPSE_INPUT_A, --timelapse-input-A TIMELAPSE_INPUT_A
                       如果您想要一个延时：需要配置输入文件夹，此文件夹应包含A脸以供延时转换。
                       您必须同时提供提供 --timelapse-output 和 --timelapse-input-B参数。

  -tib TIMELAPSE_INPUT_B, --timelapse-input-B TIMELAPSE_INPUT_B
                       如果您想要一个延时：需要配置输入文件夹，此文件夹应包含B脸以供延时转换。
                       您必须同时提供提供 --timelapse-output 和 --timelapse-input-A参数。

  -to TIMELAPSE_OUTPUT, --timelapse-output TIMELAPSE_OUTPUT
                       延时的输出文件夹。如果输入设置了文件夹，但没有输出文件夹，
                       它将默认为model/timelapse/



【faceswap.py  convert】  使用faceswap.py文件，将源图像转换为换脸的新图像。
usage: faceswap.py convert [-h] [-L {INFO,VERBOSE,DEBUG,TRACE}] [-LF LOGFILE]
                           [-i INPUT_DIR] [-o OUTPUT_DIR]
                           [-al ALIGNMENTS_PATH] [-l REF_THRESHOLD]
                           [-n NFILTER [NFILTER ...]] [-f FILTER [FILTER ...]]
                           [-m MODEL_DIR] [-a INPUT_ALIGNED_DIR]
                           [-t {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}]
                           [-c {Masked,Adjust}] [-b BLUR_SIZE]
                           [-e EROSION_KERNEL_SIZE]
                           [-M {rect,facehull,facehullandrect}]
                           [-sh {bsharpen,gsharpen}] [-g GPUS]
                           [-fr FRAME_RANGES [FRAME_RANGES ...]] [-d] [-s]
                           [-S] [-mh] [-sm] [-aca] [-dt]

optional arguments:
  -h, --help            显示帮助的信息，然后返回。

  -L {INFO,VERBOSE,DEBUG,TRACE}, --loglevel {INFO,VERBOSE,DEBUG,TRACE}
                        配置日志级别。除非你需要提交故障报告，否则请坚持用INFO或VERBOSE来提供信息或详细信息。
                        在使用TRACE参数时特别注意，因为它会产生很多的数据。

  -LF LOGFILE, --logfile LOGFILE
                        配置日志文件路径。留空的话，会在faceswap文件夹中生成日志。
 
  -i INPUT_DIR, --input-dir INPUT_DIR
                        配置输入目录或者视频。需要含有你想处理的图像或视频的路径。默认需要输入。 

  -o OUTPUT_DIR, --output-dir OUTPUT_DIR
                        配置输出目录。这是转换后文件的存储位置。默认要“输出”

  -al ALIGNMENTS_PATH, --alignments ALIGNMENTS_PATH
                        配置文件的路径。

  -l REF_THRESHOLD, --ref_threshold REF_THRESHOLD
                        面部的识别阈值

  -n NFILTER [NFILTER ...], --nfilter NFILTER [NFILTER ...]
                        配置不想被特征提取的图片过滤器。要求是正面的图像。多张图片可用空格分割。 

  -f FILTER [FILTER ...], --filter FILTER [FILTER ...]
                       配置想被特征提取的图片过滤器。要求是正面的图像。多张图片可用空格分割。

  -m MODEL_DIR, --model-dir MODEL_DIR
                        配置模型的目录。这个目录需要含有已经你想处理的的，已经训练了的模型。默认为'models'目录。

  -a INPUT_ALIGNED_DIR, --input-aligned-dir INPUT_ALIGNED_DIR
	                配置输入的“校准目录”。这个目录应该包含从输入中提取的已经校准过的人脸。
                        如果从该文件夹中删除了人脸，它们将在转换期间跳过。
                        如果没有指定对齐的目录，将转换所有人脸。
                       
  -t {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}, --trainer {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}
                       选择模型创建时候的训练算法

  -c {Masked,Adjust}, --converter {Masked,Adjust}
                       配置要使用的转换器（masked 蒙版层，adjust 调整层）

  -b BLUR_SIZE, --blur-size BLUR_SIZE
                        边缘羽化尺寸.  (只适用于蒙版层转化 )

  -e EROSION_KERNEL_SIZE, --erosion-kernel-size EROSION_KERNEL_SIZE
                        图像腐蚀和膨胀参数。
                        正值用于腐蚀，减少了交换面的边缘。
                        负值用于膨胀，允许交换的面覆盖更多空间。
                        (只适用于蒙版层转化 )

  -M {rect,facehull,facehullandrect}, --mask-type {rect,facehull,facehullandrect}
                        蒙版用于置换人脸(只适用于蒙版层转化 )

  -sh {bsharpen,gsharpen}, --sharpen {bsharpen,gsharpen}
                        使用锐化图像。bsharpen用于像素模糊，gsharpen用于高斯模糊(只适用于蒙版层转化 )

  -g GPUS, --gpus GPUS  
                        设置用于转换的GPU数量

  -fr FRAME_RANGES [FRAME_RANGES ...], --frame-ranges FRAME_RANGES [FRAME_RANGES ...]
                       应用传输的帧范围。
                       例如帧10到50和90到100使用的方法"--frame-ranges 10-50 90-100"。
                       文件名中的最后一个编号必须是帧编号。
                  
  -d, --discard-frames  
                       当使用" --frame-ranges"参数的时候，使用"-d"参数来忽略特定的帧处理，让这些帧原封不动的写出。

  -s, --swap-model     
                      互换模型，用 B -> A来代替 A -> B 

  -S, --seamless        
                      使用CV2的无缝克隆。(只适用于蒙版层转化 )

  -mh, --match-histogram
                       使用直方图匹配。(只适用于蒙版层转化 )

  -sm, --smooth-mask    
                       平滑蒙版(只适用于调整层)

  -aca, --avg-color-adjust
                       色调均衡调整(只适用于调整层)

  -dt, --draw-transparent
                       将交换的面放置在透明层上，而不是原始帧上。


usage: faceswap.py gui [-h] [-L {INFO,VERBOSE,DEBUG,TRACE}] [-LF LOGFILE] [-d]

Launch the Faceswap Graphical User Interface

optional arguments:
  -h, --help            show this help message and exit
  -L {INFO,VERBOSE,DEBUG,TRACE}, --loglevel {INFO,VERBOSE,DEBUG,TRACE}
                        Log level. Stick with INFO or VERBOSE unless you need
                        to file an error report. Be careful with TRACE as it
                        will generate a lot of data
  -LF LOGFILE, --logfile LOGFILE
                        Path to store the logfile. Leave blank to store in the
                        faceswap folder
  -d, --debug           Output to Shell console instead of GUI console


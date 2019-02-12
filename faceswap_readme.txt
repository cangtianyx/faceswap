��faceswap.py [-h]��

��������: {extract,train,convert,gui}
    extract            ��ͼƬ����ȡ�沿����
    train               ѵ��һ��ģ�ͣ�����ʶ��A��B��������
    convert           ʹ��ѵ����ģ�ͣ��û�ԭͼƬ�������µ��沿��
    gui                  ����ͼ�ν�������faceswap


��faceswap.py extract����ͼƬ����ȡ��������
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
            ��ʾ��������ϢȻ���˳�
  -L {INFO,VERBOSE,DEBUG,TRACE}, --loglevel {INFO,VERBOSE,DEBUG,TRACE}
            ������־���𡣳�������Ҫ�ύ���ϱ��棬����������INFO��VERBOSE���ṩ��Ϣ����ϸ��Ϣ��
            ��ʹ��TRACE����ʱ�ر�ע�⣬��Ϊ��������ܶ�����ݡ�

  -LF LOGFILE, --logfile LOGFILE           
            �洢��־�ļ���·�����������ձ�����FACESWAP�ļ��С�
                     
  -i INPUT_DIR, --input-dir INPUT_DIR
            ����Ŀ¼����Ƶ��Ŀ¼����Ҫ�����ͼ���ļ���·������Ƶ�ļ���Ĭ��Ϊ��input����
                       
  -o OUTPUT_DIR, --output-dir OUTPUT_DIR
            ���Ŀ¼������ת���ļ���λ�ý����洢��Ĭ��Ϊ��output����
                       
  -al ALIGNMENTS_PATH, --alignments ALIGNMENTS_PATH
            �����ļ���·�����á�
                      
  -l REF_THRESHOLD, --ref_threshold REF_THRESHOLD
            �沿ʶ����ֵ
                        
  -n NFILTER [NFILTER ...], --nfilter NFILTER [NFILTER ...]
            ���ò��뱻������ȡ��ͼƬ��������Ҫ���������ͼ�񡣶���ͼƬ���ÿո�ָ

  -f FILTER [FILTER ...], --filter FILTER [FILTER ...]
            ����ָ���Ĺ���������ͼƬ������ȡ��Ҫ��������ͼ�񣬶���ͼƬ���ÿո�ָ 

  --serializer {json,pickle,yaml}
            �����ļ������и�ʽ�����yaml��ʽ��ѡ�����û�м����ôjson��ʽ���ڻش��б�ʹ�á�
   
  -D {dlib-cnn,dlib-hog,mtcnn}, --detector {dlib-cnn,dlib-hog,mtcnn}
            Ҫʹ�õ�̽�������͡�              
                ��dlib hog����ʹ�����ٵ���Դ������ɿ��ġ�
                ��dlib cnn������mtcnn�죬����⵽���ٵ���׺͸��ٵļ����ԡ�
                ��mtcnn������dlib������ʹ�ý�����Դ��ͬʱ�����������͸����󱨡������ƿ���DLIB

  -A {dlib,fan}, --aligner {dlib,fan}
           ��ȡ����ѡ��
                ��dlib"��dlib��̬��⡣Ѹ�١����ٵ���Դռ�ã�����׼ȷ
                  "fan"���������磬������ع⣬��GPU��Դռ�д�  

  -mtms MTCNN_MINSIZE, --mtcnn-minsize MTCNN_MINSIZE
           �沿ʶ�����С����ֵ����ֵ���ķѸ�����ڴ档���ֵΪ10��Ĭ��Ϊ20��

  -mtth MTCNN_THRESHOLD [MTCNN_THRESHOLD ...], --mtcnn-threshold MTCNN_THRESHOLD [MTCNN_THRESHOLD ...]
           �沿����������ֵ��ÿһ��ֵ����Ҫ����1 ������'--mtcnn-threshold 0.6 0.7 0.7'.
                  ��һ���������Ȼ�ɼ����沿
                  �ڶ������ᴿ�沿����ֵ
                  ����������һ��ϸ���沿��ѡ
                  Ĭ��ֵΪ 0.6 0.7 0.7

  -mtsc MTCNN_SCALEFACTOR, --mtcnn-scalefactor MTCNN_SCALEFACTOR
            ͼ���������õı���������Ӧ����С��1��ʮ��������Ĭ��ֵΪ0.709������ʹ��MTCNNʱ��Ч��

  -r ROTATE_IMAGES, --rotate-images ROTATE_IMAGES
            ����תͼ������������Ҳ�������������תͼ���Գ��Լ�⡣
            ������ܿ����ҵ��������ף�����������ȡ�ٶ�Ϊ���ۡ�
            ʹ��ǰ��Ҫ����һ�����֡����������ֵΪ360����ͨ���б���Ծ�ȷö��Ҫ���ĽǶ�ֵ��
 
 -bt BLUR_THRESH, --blur-threshold BLUR_THRESH
            ����ģ���ٽ�ֵ���ڼ��ʱ������Ƭ��������ͼ���ƶ�����Ϊ��blurry�������ļ��С����õ�ֵԽС�������ģ����Խ��
                  
  -mp, --multiprocess   
             ���߳���ȡ���á�������һЩ��ȡ���ʱ���٣���������һЩ��ֻ��������GPU��ʱ�����Ч�����������Զ��ġ�

  -sz SIZE, --size SIZE
             ������沿��С��ȷ����������ѵ��ģ�ͣ�֧��������ĳߴ硣������ĸ�������ڸ߷ֱ���ģ�͡�

  -s, --skip-existing  
             �����������ļ����Ѿ����ڵ���ȡ֡��

  -sf, --skip-existing-faces
             �����������ļ����Ѿ����ڵ��沿֡��

  -dl, --debug-landmarks
             ��������ϻ��Ʊ�־�Խ��е���
  
  -ae, --align-eyes     
             ���ж���У׼��ȷ������/���۵ȸ�

  -si SAVE_INTERVAL, --save-interval SAVE_INTERVAL
            ���������ļ��Զ���������
            ��һ��֡����ȡ����Զ������������ļ��С�Ĭ���������ű��档
            ���棺��Ҫ��д���ļ���ʱ���жϽű���Ϊ���ܻ�����𻵡�
                       
��faceswap.py  train��ѵ��һ��ģ�ͣ�����ʶ��A��B������
usage: faceswap.py train [-h] [-L {INFO,VERBOSE,DEBUG,TRACE}] [-LF LOGFILE]
                         [-A INPUT_A] [-B INPUT_B] [-m MODEL_DIR]
                         [-s SAVE_INTERVAL]
                         [-t {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}]
                         [-bs BATCH_SIZE] [-it ITERATIONS] [-g GPUS] [-p] [-w]
                         [-pl] [-ag] [-tia TIMELAPSE_INPUT_A]
                         [-tib TIMELAPSE_INPUT_B] [-to TIMELAPSE_OUTPUT]

��������:
  -h, --help            
                        ��ʾ��������Ϣ��Ȼ�󷵻ء�
  -L {INFO,VERBOSE,DEBUG,TRACE}, --loglevel {INFO,VERBOSE,DEBUG,TRACE}
                        ������־���𡣳�������Ҫ�ύ���ϱ��棬����������INFO��VERBOSE���ṩ��Ϣ����ϸ��Ϣ��
                        ��ʹ��TRACE����ʱ�ر�ע�⣬��Ϊ��������ܶ�����ݡ�

  -LF LOGFILE, --logfile LOGFILE
                        ������־�ļ�·�������յĻ�������faceswap�ļ�����������־��

  -A INPUT_A, --input-A INPUT_A
                       ����A��������Ŀ¼����Ҫ�ṩ����A����ѵ��ͼƬ��Ŀ¼������ѵ��A����Ĭ����Ҫ���롣

  -B INPUT_B, --input-B INPUT_B
                       ����B��������Ŀ¼����Ҫ�ṩ����A����ѵ��ͼƬ��Ŀ¼������ѵ��A����Ĭ����Ҫ���롣

  -m MODEL_DIR, --model-dir MODEL_DIR
                       ����ѵ��ģ�͵�����Ŀ¼�����ĵ�û����ѵ�����ݡ�Ĭ����Ҫ���롣 

  -s SAVE_INTERVAL, --save-interval SAVE_INTERVAL
                       ������Ҫ�����ģ�͵���ֵ��

  -t {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}, --trainer {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}
                       ѡ��ѵ��ģʽ��ʹ��LowMemģʽ����ѵ���Ļ�����Ҫ���Կ��ڴ����2GB��

  -bs BATCH_SIZE, --batch-size BATCH_SIZE
                        ������ߴ�,��Ҫʱ2��������������(64, 128, 256, �ȵ�)

  -it ITERATIONS, --iterations ITERATIONS
                        �ظ�ѵ���Ĵ���

  -g GPUS, --gpus GPUS  
                        ���ö���GPU����������ѵ��

  -p, --preview        
                        ��ʾ���Ԥ�������û�����ã��ͽ�����д���ļ��� 

  -w, --write-image     
                        ��ʹ��Ԥ��ģʽ��ҲҪ��ѵ�����д�뵽�ļ���

  -pl, --use-perceptual-loss
                       ʹ���޸�ģʽ����ѵ��

  -ag, --allow-growth   
                       ������������Tensorflow���ԺķѶ��ٱ����ڴ�

  -tia TIMELAPSE_INPUT_A, --timelapse-input-A TIMELAPSE_INPUT_A
                       �������Ҫһ����ʱ����Ҫ���������ļ��У����ļ���Ӧ����A���Թ���ʱת����
                       ������ͬʱ�ṩ�ṩ --timelapse-output �� --timelapse-input-B������

  -tib TIMELAPSE_INPUT_B, --timelapse-input-B TIMELAPSE_INPUT_B
                       �������Ҫһ����ʱ����Ҫ���������ļ��У����ļ���Ӧ����B���Թ���ʱת����
                       ������ͬʱ�ṩ�ṩ --timelapse-output �� --timelapse-input-A������

  -to TIMELAPSE_OUTPUT, --timelapse-output TIMELAPSE_OUTPUT
                       ��ʱ������ļ��С���������������ļ��У���û������ļ��У�
                       ����Ĭ��Ϊmodel/timelapse/



��faceswap.py  convert��  ʹ��faceswap.py�ļ�����Դͼ��ת��Ϊ��������ͼ��
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
  -h, --help       ��ʾ��������Ϣ��Ȼ�󷵻ء�

  -L {INFO,VERBOSE,DEBUG,TRACE}, --loglevel {INFO,VERBOSE,DEBUG,TRACE}
                        ������־���𡣳�������Ҫ�ύ���ϱ��棬����������INFO��VERBOSE���ṩ��Ϣ����ϸ��Ϣ��
                        ��ʹ��TRACE����ʱ�ر�ע�⣬��Ϊ��������ܶ�����ݡ�

  -LF LOGFILE, --logfile LOGFILE
                        ������־�ļ�·�������յĻ�������faceswap�ļ�����������־��
 
  -i INPUT_DIR, --input-dir INPUT_DIR
                        ��������Ŀ¼������Ƶ����Ҫ�������봦���ͼ�����Ƶ��·����Ĭ����Ҫ���롣 

  -o OUTPUT_DIR, --output-dir OUTPUT_DIR
                        �������Ŀ¼������ת�����ļ��Ĵ洢λ�á�Ĭ��Ҫ�������

  -al ALIGNMENTS_PATH, --alignments ALIGNMENTS_PATH
                        �����ļ���·����

  -l REF_THRESHOLD, --ref_threshold REF_THRESHOLD
                        �沿��ʶ����ֵ

  -n NFILTER [NFILTER ...], --nfilter NFILTER [NFILTER ...]
                        ���ò��뱻������ȡ��ͼƬ��������Ҫ���������ͼ�񡣶���ͼƬ���ÿո�ָ 

  -f FILTER [FILTER ...], --filter FILTER [FILTER ...]
                       �����뱻������ȡ��ͼƬ��������Ҫ���������ͼ�񡣶���ͼƬ���ÿո�ָ

  -m MODEL_DIR, --model-dir MODEL_DIR
                        ����ģ�͵�Ŀ¼�����Ŀ¼��Ҫ�����Ѿ����봦��ĵģ��Ѿ�ѵ���˵�ģ�͡�Ĭ��Ϊ'models'Ŀ¼��

  -a INPUT_ALIGNED_DIR, --input-aligned-dir INPUT_ALIGNED_DIR
	        ��������ġ�У׼Ŀ¼�������Ŀ¼Ӧ�ð�������������ȡ���Ѿ�У׼����������
                        ����Ӹ��ļ�����ɾ�������������ǽ���ת���ڼ�������
                        ���û��ָ�������Ŀ¼����ת������������
                       
  -t {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}, --trainer {GAN128,LowMem,IAE,Original,OriginalHighRes,GAN}
                       ѡ��ģ�ʹ���ʱ���ѵ���㷨

  -c {Masked,Adjust}, --converter {Masked,Adjust}
                       ����Ҫʹ�õ�ת������masked �ɰ�㣬adjust �����㣩

  -b BLUR_SIZE, --blur-size BLUR_SIZE
                        ��Ե�𻯳ߴ�.  (ֻ�������ɰ��ת�� )

  -e EROSION_KERNEL_SIZE, --erosion-kernel-size EROSION_KERNEL_SIZE
                        ͼ��ʴ�����Ͳ�����
                        ��ֵ���ڸ�ʴ�������˽�����ı�Ե��
                        ��ֵ�������ͣ����������渲�Ǹ���ռ䡣
                        (ֻ�������ɰ��ת�� )

  -M {rect,facehull,facehullandrect}, --mask-type {rect,facehull,facehullandrect}
                        �ɰ������û�����(ֻ�������ɰ��ת�� )

  -sh {bsharpen,gsharpen}, --sharpen {bsharpen,gsharpen}
                        ʹ����ͼ��bsharpen��������ģ����gsharpen���ڸ�˹ģ��(ֻ�������ɰ��ת�� )

  -g GPUS, --gpus GPUS  
                        ��������ת����GPU����

  -fr FRAME_RANGES [FRAME_RANGES ...], --frame-ranges FRAME_RANGES [FRAME_RANGES ...]
                       Ӧ�ô����֡��Χ��
                       ����֡10��50��90��100ʹ�õķ���"--frame-ranges 10-50 90-100"��
                       �ļ����е����һ����ű�����֡��š�
                  
  -d, --discard-frames  
                       ��ʹ��" --frame-ranges"������ʱ��ʹ��"-d"�����������ض���֡��������Щ֡ԭ�ⲻ����д����

  -s, --swap-model     
                      ����ģ�ͣ��� B -> A������ A -> B 

  -S, --seamless        
                      ʹ��CV2���޷��¡��(ֻ�������ɰ��ת�� )

  -mh, --match-histogram
                        ʹ��ֱ��ͼƥ�䡣(ֻ�������ɰ��ת�� )

  -sm, --smooth-mask    
                       ƽ���ɰ�(ֻ�����ڵ�����)

  -aca, --avg-color-adjust
                       ɫ���������(ֻ�����ڵ�����)

  -dt, --draw-transparent
                      ���������������͸�����ϣ�������ԭʼ֡�ϡ�


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


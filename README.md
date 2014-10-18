ZCChatAVAdioPlay
================

聊天的播放与录音
//版本说明  iOS研究院 305044955
//1.1版本 更正类名 CustomAVAdioPlay更正为ZCChatAVAdioPlay
//1.0版本 ZC封装的本地单例播放器（聊天版）初始创建
/*
 1、模拟器下无法调用麦克风，如果调用麦克风，会产生系统崩溃
 2、主要用在聊天界面进行语音播放使用，用于录音+转换格式+保存，加清空缓存，以及语音转码
 3、为什么要转码，因为苹果默认是WAV文件相对比较大，进行转码后的AMR格式比转之前小10倍
 4、本类特点是调用的方法少，很多使用Block进行回调
 */
/*
 需要添加的支持库
 AVFoundation
 第三方
 Base64（音频转文字）、
 amr_wav（格式互转）2个文件夹
 录音需要真机才可以进行，模拟器会自动判断不启动录音
 */
/*
 代码示例
 //开始录音
 ZCChatAVAdioPlay*avAdio=[ZCChatAVAdioPlay sharedInstance];
 [avAdio startRecording];
 
 //结束录音
 ZCChatAVAdioPlay*avAdio=[ZCChatAVAdioPlay sharedInstance];
 [avAdio endRecordingWithBlock:^(NSString *aa) {
 NSLog(@"amr转码base64，可以进行发送数据%@",aa);
 }];
 
 //播放声音
 NSArray*file=[ZCChatAVAdioPlay getVoiceFileName];
 NSLog(@"获取文件夹下目录%@",file);
 //读取出amr文件名
 NSString*last=[file objectAtIndex:file.count-2];
 //拼接路径
 NSString*path=[NSString stringWithFormat:@"%@/Library/Caches/Voice/%@",NSHomeDirectory(),last];
 NSLog(@"Main~%@",path);
 //读取文件
 NSData*data=[NSData dataWithContentsOfFile:path];
 ZCChatAVAdioPlay*av=[ZCChatAVAdioPlay sharedInstance];
 //播放
 [av playSetAvAudio:data];
 
 */

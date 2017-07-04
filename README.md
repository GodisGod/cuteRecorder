
###自定义录音工具类：
custom recorder util:

###HOW to：

###Step 1. Add the JitPack repository to your build file
Add it in your root build.gradle at the end of repositories:

	allprojects {
		repositories {
			...
			maven { url 'https://www.jitpack.io' }
		}
	}
###Step 2. Add the dependency

	dependencies {
	        compile 'com.github.GodisGod:cuteRecorder:v1.0.0'
	}
  
  
ex:

        private CuteRecorder recorder;   //构建对象
        recorder = new CuteRecorder.Builder()
                .maxTime(60)   //最大录制时间
                .minTime(3)    //最短录制时间
                .outPutDir(outPutDir) //输出录音文件路径
                .voiceLevel(CuteRecorder.NORMAL)//最大音量
                .build();
                
       //设置监听
        recorder.setOnAudioRecordListener(new CuteRecorder.AudioRecordListener() {
            @Override
            public void hasRecord(int seconds) {
               //已录制时间
            }

            @Override
            public void finish(int seconds, final String filePath) {
              //录制完成 返回录制时间和录音文件路径
            }

            @Override
            public void tooShort() {
               //录音时间太短
            }

            @Override
            public void curVoice(final int voice) {
              //根据传入的最大音量计算出的当前音量
            }
        });


### px、dp相互转换

```
public class DensityUtil {
```

```
    /**
     * 根据手机的分辨率从 dp 的单位 转成为 px(像素)
     */
    public static int dip2px(Context context, float dpValue) {
        final float scale = context.getResources().getDisplayMetrics().density;
        return (int) (dpValue * scale + 0.5f);
    }

    /**
     * 根据手机的分辨率从 px(像素) 的单位 转成为 dp
     */
    public static int px2dip(Context context, float pxValue) {
        final float scale = context.getResources().getDisplayMetrics().density;
        return (int) (pxValue / scale + 0.5f);
    }
}
```

### 获取屏幕宽高

```
Resources resources = this.getResources();
DisplayMetrics dm = resources.getDisplayMetrics();
float density1 = dm.density;
int width = dm.widthPixels;
int height = dm.heightPixels;
```

### 获取codec

```
private List<String> mSupportedCodecs;
private void getSupportedCodecs() {
    int numCodecs = MediaCodecList.getCodecCount();
    mSupportedCodecs = new ArrayList<String>(numCodecs);
    for (int i = 0; i < numCodecs; i++) {
        MediaCodecInfo codecInfo = MediaCodecList.getCodecInfoAt(i);
        mSupportedCodecs.add(codecInfo.getName());
    }
}
```

### 开机焦点问题
```
public class TouchModeUtils {

    /**
     * 开机时系统处于touch mode，需要手动发送一个按键事件。
     */
    public static void doKeyActionInTouchMode() {
        new Thread() {
            public void run() {
                try {
                    Instrumentation inst = new Instrumentation();
                    inst.sendKeyDownUpSync(KeyEvent.KEYCODE_SLASH);
                    inst.setInTouchMode(false);
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
        }.start();
    }
}
```
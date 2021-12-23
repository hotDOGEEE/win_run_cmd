# win_run_cmd


```
import subprocess
import multiprocessing


def back_command(cmd):
    p = subprocess.Popen(cmd, shell=True, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
    p.wait()


if __name__ == '__main__':

    pool = multiprocessing.Pool(multiprocessing.cpu_count())
    rst = [pool.apply_async(back_command, args=(r"adb logcat",)) for i in range(multiprocessing.cpu_count())]
    rst[0].wait()
```


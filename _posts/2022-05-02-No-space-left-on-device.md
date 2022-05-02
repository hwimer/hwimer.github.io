---
title: No space left on device
categories: 
    - troubleShooting
    - Java 
---

### 문제발생:
> "No space left on device"

```text
2022-04-28 15:15:22.845 [org.springframework.scheduling.quartz.SchedulerFactoryBean#0_Worker-8] WARN  c.a.s.s.i.S3AbortableInputStream - Not all bytes were read from the S3ObjectInputStream, aborting HTTP connection. This is likely an error and may result in sub-optimal behavior. Request only the bytes you need via a ranged GET or drain the input stream after use.
2022-04-28 15:15:23.036 [org.springframework.scheduling.quartz.SchedulerFactoryBean#0_Worker-8] WARN  c.a.s.s.i.S3AbortableInputStream - Not all bytes were read from the S3ObjectInputStream, aborting HTTP connection. This is likely an error and may result in sub-optimal behavior. Request only the bytes you need via a ranged GET or drain the input stream after use.
2022-04-28 15:15:23.036 [org.springframework.scheduling.quartz.SchedulerFactoryBean#0_Worker-8] ERROR c.i.g.i.f.s.s.IntegrateKNPUServiceImpl - ERROR
java.io.IOException: No space left on device
        at java.io.FileOutputStream.writeBytes(Native Method)
        at java.io.FileOutputStream.write(FileOutputStream.java:326)
        at org.apache.commons.io.IOUtils.copyLarge(IOUtils.java:2315)
        at org.apache.commons.io.IOUtils.copy(IOUtils.java:2270)
        at org.apache.commons.io.IOUtils.copyLarge(IOUtils.java:2291)
        at org.apache.commons.io.IOUtils.copy(IOUtils.java:2246)
```

### 원인: 
> 사내 파일을 업로드하는 수집서버에 오류가 발생하였다.<br>
> 현재 사내수집서버는 로드밸런싱에의해 4중화 되어있는 상태이며, <br>
> 사내 서버로 업로드되는 모든파일들은 업무상 공유가 되어야만한다. <br>
> 그래서 Network File System같은 파일공유 시스템을 사용해야하며 AWS가 제공하는 EFS를 사용했다.
> 그러나 EFS비용이점차 많이나오는 문제가 발생하였고, EFS에서 S3(AWS)로 스토리지 서비스로 변경하였다. <br><br>
> 기존 efs를 사용했을때는 파일저장시 마치, 내 로컬에 저장하듯이 적재했어서 따로 지울일이 없었는데
> 이번에 S3로 변경하게되면서 S3Library를 통해 버킷에 적재 후 업로드가 완료된(로컬에 남은)파일을 
> 지우지 않아 각 인스턴스마다 용량이차 "No space left on device" 오류가 발생하였다. <br>


### 해결 : 
> 파일업로드가 끝난 파일들은 <br>
> 업로드가 종료된부분에서 File.delete() 를통해 모두 삭제해주었습니다.

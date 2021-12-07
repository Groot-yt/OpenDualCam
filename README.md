# OpenDualCam
实现原理是：
先获取到所有的逻辑摄像头（manager.getCameraIdList()）,
然后通过逻辑摄像头，找到对应的物理摄像头
  CameraCharacteristics cameraCharacteristics = manager.getCameraCharacteristics(id);
  Set<String> physicalCameraIds = cameraCharacteristics.getPhysicalCameraIds();
 
找到对应物理摄像头大于2的逻辑摄像头，记录下逻辑摄像头及其对应的物理摄像头的ID
  
 然后在构建输出参数时，每一个物理摄像头对应一个SurfaceTexture，构建一个OutputConfiguration对象
 最后构建一个SessionCofiguration对象，传入上面构建的两个OutputConfiguration,
 最后调用cameraDevice.createCaptureSession(sessionConfiguration);
  
 以上。

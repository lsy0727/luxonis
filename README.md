# luxonis

* 기본 연결 확인
```
python -c "import depthai as dai; print('Available devices:', [dai.DeviceInfo() for _ in dai.Device.getAllAvailableDevices()])"
```

* 상세 연결 정보 확인
```
python -c "
import depthai as dai
devices = dai.Device.getAllAvailableDevices()
print(f'Found {len(devices)} device(s):')
for i, device in enumerate(devices):
    print(f'Device {i}: {device}')
    print(f'  - Name: {device.name}')
    print(f'  - MXID: {device.mxid}')
    print(f'  - State: {device.state}')
"
```

* 카메라별 지원 해상도 확인
```
python -c "
import depthai as dai
try:
    with dai.Device() as device:
        print('Camera connected successfully!')
        print(f'Device name: {device.getDeviceName()}')
        print(f'Bootloader version: {device.getBootloaderVersion()}')
        print(f'Device firmware: {device.getDeviceFirmware()}')
except Exception as e:
    print(f'Connection failed: {e}')
"
```

* USB 연결 상태 확인 (Windows)
```
# PowerShell에서 실행
Get-PnpDevice | Where-Object {$_.FriendlyName -like "*OAK*" -or $_.FriendlyName -like "*Luxonis*"}
```

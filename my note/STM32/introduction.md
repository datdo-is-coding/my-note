

Mục đích của khóa học
- Nắm chắc các kiến thức cơ bản về ngoại vi của STM32F103C8T6 như GPIO, EXTI, ADC, TIMER, PWM, UART,I2C
- Vận dụng được các ngoại vi vào các bài toán thực tế
- Kỹ năng debut trong quá trình phát triển
- Kỹ năng đọc mạch nguyên lý

STM32 là một trong những dòng chip phổ biến của ST với nhiều họ thông dụng như F0,F1,... F103 là lõi **ARM CORTEX M3**

**Một số ứng dụng chính** : dùng cho driver để điều khiển ứng dụng, thiết bị cầm tay, máy tính và thiết bị ngoại vi chơi game, GPS cơ bản,  các ứng dụng trong công nghiệp, thiết bị lập trình PLC, biến tần, máy in, máy quét, máy quét, hệ thống cảnh báo, thiết bị liên lạc nội bộ,.. 

**Thư viện lập trình** : STM32snippets, STM32Cube LL, STM32Cube HAL, Standard Peripheral Libraries. Mỗi thư viện có ưu và khuyết điểm riêng

**Mạch nạp** : **ULINK, J-LINK, CMSIS-DAP, STLINK**

![[Pasted image 20251019105527.png]]


Cách mắc LED theo kiểu SINK dòng và SOURCE dòng
Source dòng(source current): dòng sẽ đi từ chân vi điều khiển và xuống GND.
Sink dòng (sink current): dòng sẽ đi từ nguồn qua tải về chân vi điều khiển và xuống đất
![[Pasted image 20251017214909.png]]![[Pasted image 20251017215010.png]]

`HAL_GPIO_WritePin(GPIOC,GPIO_PIN_13,GPIO_P`
`HAL_Delay(1000)`

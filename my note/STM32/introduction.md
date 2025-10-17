Mục đích của khóa học
- Nắm chắc các kiến thức cơ bản về ngoại vi của STM32F103C8T6 như GPIO, EXTI, ADC, TIMER, PWM, UART,I2C
- Vận dụng được các ngoại vi vào các bài toán thực tế
- Kỹ năng debut trong quá trình phát triển
- Kỹ năng đọc mạch nguyên lý

Cách mắc LED theo kiểu SINK dòng và SOURCE dòng
Source dòng(source current): dòng sẽ đi từ chân vi điều khiển và xuống GND.
Sink dòng (sink current): dòng sẽ đi từ nguồn qua tải về chân vi điều khiển và xuống đất
![[Pasted image 20251017214909.png]]![[Pasted image 20251017215010.png]]

`HAL_GPIO_WritePin(GPIOC,GPIO_PIN_13,GPIO_P`
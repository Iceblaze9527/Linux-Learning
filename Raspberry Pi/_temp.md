### 1.2 I2C-Tools
I2C-Tools are utilities for ease of monitoring and identifying I2C devices. These tools are also important for fault diagnosis. You can get the tools with: `sudo apt-get install i2c-tools`

#### `i2cdetect`
 `i2cdetect` is a userspace program to scan an I2C bus for devices.
 
`i2cdetect -y 1`

- `-y` Disable interactive mode. By default, `i2cdetect` will wait for a confirmation from the user before messing with the I2C bus. When this flag is used, it will perform the operation directly.
- `1` Indicates the number or name of the I2C bus to be scanned.

#### `i2cdump`
`i2cdump` is a small helper program to examine registers visible through the I2C bus.

`i2cdump -y 1 0x68`

-   `-y` Disable interactive mode. By default, `i2cdump` will wait for a confirmation from the user before messing with the I2C bus. When this flag is used, it will perform the operation directly.
-   `1` Indicates the number or name of the I2C bus to be scanned.
-  ` 0x68` Indicates the address to be scanned on that bus.

#### `i2cset` 
`i2cset` is a small helper program to set registers visible through the I2C bus.

`i2cset -y 1 0x68 0x00 0x13`

- `-y` Disable interactive mode. By default, `i2cset` will wait for a confirmation from the user before messing with the I2C bus. When this flag is used, it will perform the operation directly.
- `1` Indicates the number or name of the I2C bus to be scanned.
- `0x68` Specifies the address of the chip on that bus.
- `0x00` Specifies the address on that chip to write to.
- `0x13` If specified, is the value to write to that location on the chip.

#### `i2cget` 
`i2cget`  is a small helper program to read registers visible through the I2C bus (or SMBus).

`i2cget -y 1 0x68 0x00`

- `-y` Disable interactive mode. By default, `i2cget` will wait for a confirmation from the user before messing with the I2C bus. When this flag is used, it will perform the operation directly.
- `1` Indicates the number or name of the I2C bus to be scanned.
- `0x68` Specifies the address of the chip on that bus.
- `0x00` Specifies the address on that chip to read from.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY2NzM3NDExMl19
-->
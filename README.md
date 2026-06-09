# STM32F103C8 EIDE + OpenOCD Template

STM32F103C8T6 project template for VS Code, Embedded IDE (EIDE), Arm GNU
Toolchain, and OpenOCD. The example blinks the common PC13 active-low LED.

## Hardware

- MCU: STM32F103C8T6
- Core clock: 72 MHz from an 8 MHz HSE
- LED: PC13
- Debug interface: SWD
- Debug probes: ST-Link by default, with a CMSIS-DAP configuration included

## Requirements

- VS Code
- Embedded IDE (`cl.eide`)
- Cortex-Debug (`marus25.cortex-debug`)
- Arm GNU Toolchain (`arm-none-eabi-gcc`)
- GNU Make
- OpenOCD

All required commands should be available in `PATH`.

On Windows, this template defaults to Arm GNU Toolchain 14.2 at:

```text
C:\Program Files (x86)\Arm GNU Toolchain arm-none-eabi\14.2 rel1
```

The path is configured for EIDE in `.vscode/settings.json` and for Make in
`Makefile`.

OpenOCD installed by WinGet is also configured with its absolute path for
Cortex-Debug and `make flash`. Open a new terminal after installation before
using the shorter `openocd` command directly.

## Build

Use the EIDE project toolbar, press `Ctrl+Shift+B`, or run:

```powershell
make
```

Outputs are written to `build/Debug/`.

## Flash

ST-Link:

```powershell
make flash
```

CMSIS-DAP:

```powershell
make flash OPENOCD_CFG=openocd/cmsis-dap.cfg
```

The EIDE uploader is configured for ST-Link.

## Debug

Open the Run and Debug panel and select either:

- `STM32F103C8 - CMSIS-DAP`
- `STM32F103C8 - ST-Link`

The launch configurations build the project before starting OpenOCD.

## Create A Project From This Template

After marking the GitHub repository as a template, select **Use this
template** on GitHub. Rename these identifiers when creating a real project:

- `.eide/eide.json`: project name and output file names
- `Makefile`: `TARGET`
- `stm32f103c8_template.ioc`: CubeMX project name, if needed

Keep the MCU definition, startup file, and linker script aligned when changing
to a different STM32F1 device.

## Upstream

Derived from the `f1_templete/st_cube_demo` example in
<https://github.com/1370773758/vscode-eide-openocd>.

STMicroelectronics source files retain their original license notices.

The **export** environment setup script creates a local.conf file without any machine selected. It is also missing a licence acceptance statement. Make the following changes before building.

- uncomment MACHINE ?= "verdin-imx8mp" and ensure no other machine is selected
- Add **"ACCEPT_FSL_EULA = "1""** at the end of the file.

My first build is core-image-full-cmdline.
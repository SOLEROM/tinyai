

## download


├── balena-etcher_1.19.16_amd64.deb
├── rk3588_spl_loader_v1.15.113.bin
├── rock-5b_bookworm_kde_b5.output.img.xz
└── rock-5b-spi-image-gd1cf491-20240523.img



unpack :
	xz -d rock-5b_bookworm_kde_b5.output.img.xz 

burn rock-5b_bookworm_kde_b5.output.img using balena-etcher_1.19.16_amd64.deb to sd


USB-C power connector should output a fixed voltage between 5V and 20V, with a power rating greater than 30W for the ROCK 5B




login:  radxa / radxa

### WSL
`wsl -l` List distros <br />
`wsl --set-default <distro-name>` Set deafault distro <br />
`wsl -u <username>` Run as specific user <br />
`wsl --set-version <distro-name> 1|2` Set distro version to 1 or 2 <br />
`wsl -t <distro-name>` Shut down distro <br />
`wsl --export --vhd <distro-name> <path-to-export-location>` Export wsl distro as a vhdx file <br />
`wsl --import --vhd <distro-name> <path-to-import-location>` Import wsl distro from a vhdx file <br />
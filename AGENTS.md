# Agent notes

- Read `README.md` and `soc.toml` first; the hardware reference pin is
  `source_revision` of `source_repository`.
- Keep `dts/sm8150.dtsi` nodes `status = "disabled"`; boards opt in per node.
- Component pins in `components.toml` must name real commits of public
  repositories; update `hardware`, `os_abi` and `verified_devices` together
  with the pin.
- Do not commit vendor firmware (SQE/GMU/ZAP binaries) or Apple artifacts.

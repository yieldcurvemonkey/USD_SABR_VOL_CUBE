# USD_SABR_VOL_CUBE

- SOFR OIS (BBG ICVS 490 curve) NVOL NY CLOSE Swaption Volatility Cube Data
- Data sourced from mix of different brokers and proprietary markings
- ATMF Stike Offsets (bps): `[-300, -250, -200, -175, -150, -125, -100, -75, -50, -35, -25, -15, -10, -5, 0, 5, 10, 15, 25, 35, 50, 75, 100, 125, 150, 175, 200, 250, 300]`
- SABR Model calibrated using [Differential Evolution](https://en.wikipedia.org/wiki/Differential_evolution) with a Residual Sum of Squares objective function and a refinement using simple Gauss-Newton to minimize the weighted root mean square error in implied volatilities as described in `Le Floc’h` + `Kennedy`'s [Explicit SABR Calibration through Simple Expansions](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2467231)
- [Bilinear interpolation](https://en.wikipedia.org/wiki/Bilinear_interpolation) in log-space (to avoid negative vols when extrapolating) is used

- Schema for EOD JSON file:

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "USD SABR VOL CUBE NVOL NY CLOSE",
  "description": "A schema for validating swaption volatility cube data where keys represent strike offsets from the at-the-money forward (ATMF).",
  "type": "object",
  "patternProperties": {
    "^-\\d+$": {
      "description": "Strike offsets from the at-the-money forward (ATMF) in basis points. Keys are negative for strikes below ATMF.",
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "Expiry": {
            "type": "string",
            "description": "The tenor of the option (e.g., '1M', '3M', '6M', '1Y', etc.)."
          },
          "1Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 1-year maturity."
          },
          "2Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 2-year maturity."
          },
          "3Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 3-year maturity."
          },
          "4Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 4-year maturity."
          },
          "5Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 5-year maturity."
          },
          "6Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 6-year maturity."
          },
          "7Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 7-year maturity."
          },
          "8Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with an 8-year maturity."
          },
          "9Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 9-year maturity."
          },
          "10Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 10-year maturity."
          },
          "15Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 15-year maturity."
          },
          "20Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 20-year maturity."
          },
          "25Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 25-year maturity."
          },
          "30Y": {
            "type": "number",
            "description": "Normal Volatility value for a swap with a 30-year maturity."
          }
        },
        "required": ["Expiry"],
        "additionalProperties": false
      }
    }
  },
  "additionalProperties": false
}
```

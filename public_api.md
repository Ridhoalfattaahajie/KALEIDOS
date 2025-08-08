# 📖 Public API — KALEIDOS IMMUNOCORE

> Version: v0.1.0  
> Status: Experimental — For Testing & Feedback Only

This document provides a high-level description of the public methods available in the KALEIDOS IMMUNOCORE framework. These APIs are designed to allow external systems to interact with the core features without exposing the internal architecture or proprietary logic.

---

## 🔹 `KALEIDOSEPRCore()`

**Description:**  
Initialize the core analysis engine for KALEIDOS IMMUNOCORE. This object acts as the entry point for risk evaluation and anomaly processing.

**Example Usage:**
```python
from kaleidos_epr_core import KALEIDOSEPRCore

engine = KALEIDOSEPRCore(config_path="configs/kaleidos_omega_patch.yaml")

Parameters:

config_path (str): Path to the YAML configuration file.


Returns:
Instance of the KALEIDOS core class.


---

🔹 engine.process_contract(bytecode: str, metadata: dict = None)

Description:
Feeds a smart contract bytecode into the analysis pipeline and returns the resulting fingerprint and threat matrix.

Parameters:

bytecode (str): The compiled smart contract bytecode.

metadata (dict, optional): Optional additional information (e.g. compiler version, network info).


Returns:

{
  "fingerprint_hash": "<sha256>",
  "anomaly_score": 0.812,
  "severity_rating": "HIGH",
  "xi_map": [...],  # abstracted
  "explanation": "Detected probabilistic anomaly near opcode pattern group 0x4b*"
}


---

🔹 engine.visualize_fingerprint(output_path: str)

Description:
Generate a visual representation of the xi-fingerprint in 3D space.

Parameters:

output_path (str): File path to save the resulting visualization (PNG/HTML).


Returns:
None. (Creates visual file on disk.)


---

🔹 engine.get_confidence_interval()

Description:
Returns the confidence interval derived from entropy-informed calibration.

Returns:

{
  "lower_bound": 0.74,
  "upper_bound": 0.91,
  "lambda_eff": 0.872
}


---

🔹 engine.export_report(format: str = "json")

Description:
Exports the full analysis result in the selected format.

Parameters:

format (str): "json", "yaml", or "txt".


Returns:

str or dict: The report content, depending on format.



---

🔹 engine.calibrate(thresholds: dict = None)

Description:
Recalibrates internal detection thresholds. Optional custom values can be provided.

Parameters:

thresholds (dict, optional): Custom alpha/beta parameters.


Returns:
Boolean indicating whether recalibration was successful.


---

🛑 Disclaimer

The public API is limited and controlled. Deeper access to internals such as probabilistic embedding, fingerprint hashing mechanisms, or patch estimators is restricted under the IP scope of the KALEIDOS project.

For advanced integrations, research licensing, or PoC evaluations, please contact the maintainers.

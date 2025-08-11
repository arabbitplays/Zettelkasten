**Costs:**

$$cost\ of\ IC = \frac{cost\ of\ dies + die\ tests + packaging + IC\ tests}{yield\ after\ tests}$$
$$cost\ of\ dies = \frac{cost\ of\ wafers}{dies\ per\ wafer * yield}$$
$$dies\ per\ wafer = \frac{\pi * (0,5*diameter\ of\ wafer)^2}{area\ of\ die}-\frac{\pi * diameter\ of\ wafer}{\sqrt{2*area\ of\ die}}$$
$$die\ yield = wafer\ yield / (1 + defects\ per\ area * die\ area)^N$$

**Benchmarks:**
$$SPECratio_x = \frac{ReferenceTime_x}{Runtime_x}$$
$$\sqrt[n]{\prod_i^n SPECratio_i}$$
$$SPECrate = m_x * SPECratio$$
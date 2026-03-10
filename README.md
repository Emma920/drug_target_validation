This is a pipeline used for selecting potential drug targets for RLT, the scoring system is as follows:

╔══════════════════════════════════════════════════════════════════════════════╗
║                           SCORING REFERENCE                                  ║
╚══════════════════════════════════════════════════════════════════════════════╝

│ ANTIBODY SCORING                                                             │
│                                                                              │
│ Factors included:                                                            │
│ • Membrane Accessibility (45%) - Can antibody reach the target?              │
│ • Extracellular Domain (35%) - Is there enough surface to bind?              │
│ • Clinical Precedence (20%) - Have antibodies worked before?                 │
│                                                                              │
│ Factors NOT included:                                                        │
│ ✗ Binding pocket (not relevant for antibodies)                              │
│ ✗ GPCR status (not relevant for antibodies)                                 │
│ ✗ Internalization (not needed for antibody-only)                            │
│                                                                              │
│ Approved Drugs: Shown but NOT scored (informational)                        │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ PEPTIDE SCORING                                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│ Factors included:                                                            │
│ • Receptor Status (40%) - Is it a GPCR/receptor? (peptide targets)          │
│ • Binding Pocket (35%) - Is there a pocket for peptide to bind?             │
│ • Binding Data (25%) - Is binding proven (Ki/Kd)?                           │
│                                                                              │
│ Factors NOT included:                                                        │
│ ✗ Membrane type (not relevant - peptides bind to structure)                 │
│ ✗ Extracellular domain size (not relevant)                                  │
│ ✗ GPI-anchored status (not relevant)                                        │
│                                                                              │
│ Approved Drugs: Shown but NOT scored (informational)                        │
└──────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────┐
│ ADC SCORING                                                                  │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│ Factors included:                                                            │
│ • Surface Accessibility (50%) - Can antibody reach target?                  │
│ • Internalization (50%) - Will it enter the cell with payload?              │
│                                                                              │
│ Factors NOT included:                                                        │
│ ✗ Tumor selectivity (removed per request)                                   │
│ ✗ Binding pocket (not relevant for ADC mechanism)                           │
│                                                                              │
│ Approved Drugs: Shown but NOT scored (informational)                        │
└──────────────────────────────────────────────────────────────────────────────┘

╔══════════════════════════════════════════════════════════════════════════════╗
║                        DETAILED SCORING TABLES                               ║
╚══════════════════════════════════════════════════════════════════════════════╝

ANTIBODY - Membrane Accessibility:
──────────────────────────────────
Type I TM           = 10
Type II TM          = 10
GPI-Anchored        = 9
Secreted            = 8
4TM                 = 7
Soluble/Peripheral  = 5
GPCR                = 3
Transporter         = 3
Multi-pass          = 3
Intracellular       = 0

ANTIBODY - Extracellular Domain:
────────────────────────────────
>400 AA             = 10
250-400 AA          = 8
100-250 AA          = 6
30-100 AA           = 4
Has EC region       = 2
None                = 0

ANTIBODY - Clinical Precedence:
───────────────────────────────
Ab clinical precedence = +7
Ab tractable           = +3

═══════════════════════════════════════════════════════════════════════════════

PEPTIDE - Receptor Status:
──────────────────────────
GPCR                = 10
Other Receptor      = 7
Transporter         = 4
Other               = 0

PEPTIDE - Binding Pocket:
─────────────────────────
Active site         = +4
Binding site        = +3
Predicted pocket    = +2
Known ligands       = +1

PEPTIDE - Binding Data:
───────────────────────
Ki data             = +4
Kd data             = +3
IC50 data           = +1
3D structure        = +2

═══════════════════════════════════════════════════════════════════════════════

ADC - Surface Accessibility:
────────────────────────────
Type I/II TM        = 10
4TM                 = 7
GPI-Anchored        = 5
GPCR/Transporter    = 4
Secreted            = 0
Intracellular       = 0

ADC - Internalization:
──────────────────────
Is receptor         = +6
Type I/II TM        = +3
Multi-pass/GPCR     = +2
Has EC domain       = +1
GPI-anchored        = -2 (penalty)

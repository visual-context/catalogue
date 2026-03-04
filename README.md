# Visual Context Catalogue: Cursor Trajectories Data Library

This repository contains a data library for cursor tracking records and analysis with an interactive web interface for filtering, exploring, and exporting user interaction records.

## Project Overview

This dataset represents cursor movement data collected from a study on improving low-vision chart accessibility via on-cursor visual context. The data includes detailed interaction tracking and visualization artifacts from participants with varying visual abilities. The data is collected over three conditions: the **baseline** (using their own assistive tools), **Mini-map** an augmentation of a small overview around the cursor (with their own assistive tools), and **Dynamic Context**, an enhanced on-cursor visual context condition (with their own assistive tools). The dataset includes full cursor interaction records and time-weighted heatmaps and trajectories visualizations.

**Project Page:** https://visual-context.github.io/

## Data Files

### `full_interactions.csv`

This file contains the primary dataset of user interactions captured during the study. Each row represents a single cursor position sampling event or interaction record.

**Fields:**

| Field | Type | Description |
|-------|------|-------------|
| **ParticipantID** | String | Unique identifier for each study participant (e.g., "P1", "P2") |
| **OrderID** | Integer | The ID of the randomized and counterbalanced order of the participant (1-6) |
| **AgeGroup** | String | Participant's age group (e.g., "upper", "lower"); 40 is the cutoff age for upper/lower groups |
| **IsCongenital** | Boolean | Whether the vision condition is congenital (yes/no) |
| **LegallyBlind** | Boolean | Whether the participant is legally blind according to clinical standards (yes/no) |
| **VisualAcuity** | String | Measured visual acuity level (e.g., "low", "high"); 20/100 in the better eye is the cutoff |
| **VisualField** | String | Visual field status (e.g., "limited", "intact") |
| **ColorBlind** | Boolean | Whether the participant has color blindness (yes/no) |
| **MagnifierUser** | Boolean | Whether the participant uses a magnifier device (yes/no) |
| **ZoomLevel** | String | Zoom/magnification level settings (e.g., "low", "medium", "high"); low: < x2, medium: < x4, high: >= x4 |
| **Familiarity** | Integer | Self-reported familiarity score with charts (numeric scale, 1-5) |
*Condition** | String | Experimental condition applied during this interaction (e.g., "none", "minimap", "overview"); overview refers to Dynamic Context |
| **Content** | String | Content version of the test (e.g., "v0", "v1", "v2") |
| **QuestionID** | String | Identifier for the specific question/task being performed (e.g., "Q1", "Q5", "Q10", "Q11") |
| **Timestamp** | Integer | Unix timestamp (milliseconds) of the interaction event |
| **X** | Float | Normalized X coordinate of cursor position (0.0 to 1.0) |
| **Y** | Float | Normalized Y coordinate of cursor position (0.0 to 1.0) |

### `cursor-imaging-details.csv`

This file maps interaction records to visualization images generated from cursor movement analysis.

**Fields:**

| Field | Description |
|-------|-------------|
| **ParticipantID** | Identifier matching `full_interactions.csv` |
| **Condition** | Experimental condition applied |
| **Content** | Content version observed |
| **QuestionID** | Question identifier |
| **Heatmap** | Heatmap visualization image filename (if available) |
| **Contour** | Contour map image filename (if available) |
| **TimeWeighted** | Time-weighted trajectory image filename (if available) |
| **Scanpath** | Scanpath visualization image filename (if available) |

## Web Interface Features

The interactive catalog (`index.html`) provides the following functionality:

### **Filtering System**

Filter the visualization catalog by multiple dimensions:
- **Visualization Type:** Select by visualization category (Heatmap, Contour, TimeWeighted, FixationMap, Scanpath)
- **Participant:** Filter by specific participant IDs
- **Content:** Filter by content version (v0, v1, v2, etc.)
- **Condition:** Filter by experimental condition
- **Question:** Filter by question/task ID

Each filter category includes **All/None** quick action buttons for convenient mass selection.

### **Data Exploration**

- **Interactive Gallery:** Browse filtered visualization images with hover previews
- **Results Counter:** Real-time count of matching records based on current filters
- **Dynamic Updates:** Immediate filtering feedback as selections change

### **Download Capabilities**

- **📥 Filtered Data:** Export currently filtered results as CSV with automatic deduplication
- **📥 Full Dataset:** Download the complete interaction dataset as a single CSV file

### **Accessibility Features**

- Semantic HTML structure with proper ARIA labels
- Keyboard navigation support
- Skip-to-content link for screen readers
- Responsive design for various device sizes

## Citation

If you use this dataset or reference this project in your research, please cite:

```bibtex
@inproceedings{Sechayk2026,
  author = {Sechayk, Yotam and Rave, Hennes and R\"{a}dler, Max and Colley, Mark and Zhou, Zhongyi and Shamir, Ariel and Igarashi, Takeo},
  title = {Improving Low-Vision Chart Accessibility via On-Cursor Visual Context},
  booktitle = {Proceedings of the 2026 CHI Conference on Human Factors in Computing Systems},
  series = {CHI '26},
  year = {2026},
  month = {April},
  date = {13--17},
  location = {Barcelona, Spain},
  publisher = {ACM},
  address = {New York, NY, USA},
  pages = {21},
  doi = {10.1145/3772318.3791165}
}
```

## Study Context

This data was collected as part of research on accessibility enhancements for low-vision users interacting with data visualizations. The study examines various visual conditions and interface conditions to understand how cursor-based visual context can improve chart readability and interaction efficiency for users with visual impairments.

## Data Characteristics

- **Temporal Data:** High-frequency cursor position sampling with millisecond precision
- **User Demographics:** Diverse visual profiles including legally blind participants
- **Experimental Design:** Multiple conditions and content variations with repeated observations
- **Normalized Coordinates:** X and Y positions normalized to [0, 1] range for interface-agnostic representation

## Project Structure

```
.
├── index.html                      # Interactive web catalog
├── full_interactions.csv           # Complete interaction dataset
├── cursor-imaging-details.csv      # Visualization image mappings
├── cursor-imaging/                 # Directory containing visualization images
└── README.md                       # This file
```

## Getting Started

1. **View the Catalog:** Open `index.html` in a web browser to access the interactive interface
2. **Explore Data:** Use the filter options to find specific interactions or visualization types
3. **Download Data:** Export filtered or complete datasets for analysis
4. **Reference Images:** Access visualization images through the gallery or via the mappings in `cursor-imaging-details.csv`

## License & Attribution

For licensing and usage information, please refer to the main project page at https://visual-context.github.io/

---

**Version:** 1.0  
**Last Updated:** 2026  
**Related Publication:** CHI 2026 Conference Proceedings

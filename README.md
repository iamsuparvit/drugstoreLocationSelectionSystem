# Drugstore Location Selection System

This project automates the selection of internship placement locations (drugstores) for pharmacy students. It intelligently selects 5 nearby drugstores for each student, ensuring a realistic distribution using a weighted random selection algorithm based on geographic proximity.

## Overview

The system assigns a list of potential internship locations to students based on proximity and diversity, simulating realistic preferences.

### Algorithm Steps

1.  **Anchor Selection**: For each student, a "home" location is randomly selected from the available drugstores to serve as the center point.
2.  **Radius Search**: The system searches for other drugstores within a specific radius (default 5km) of the anchor.
3.  **Weighted Random Selection**: 5 locations are selected from the nearby group.
    *   **Closer locations** have a higher probability of being selected.
    *   This ensures students get locations near them but maintains some variety (not just the absolute closest 5).
    *   **Dynamic Expansion**: If fewer than 5 locations are found within the radius, the search radius expands automatically until enough candidates are found.

## Key Features

*   **Anchor-based Selection**: Simulates a student's residence or preferred area.
*   **Weighted Random Selection**: Uses probability weights (Closer = Higher chance) to mimic realistic preferences while adding diversity.
*   **Dynamic Radius Expansion**: Ensures every student gets the required number of options, even in sparse areas.
*   **Reproducibility**: Uses student IDs as random seeds to ensure results are consistent across runs.
*   **Analysis & Visualization**: Includes comprehensive tools to visualize geographic distribution, distance statistics, and selection frequency.

## Requirements

*   Python 3.x
*   pandas
*   numpy
*   scikit-learn (for Haversine distance)
*   matplotlib
*   seaborn
*   scipy

## Usage

1.  **Prepare Data**:
    Ensure the following files are in the project directory:
    *   `drugstore_locations.csv`: Contains drugstore data (must include `code`, `latitude`, `longitude`).
    *   `rxcu85_list_cleaned_hashed.csv`: Contains student data.

2.  **Run the Notebook**:
    Open `drugstoreLocationSelectionSystem.ipynb` and execute the cells in order.

3.  **Configuration**:
    You can adjust parameters in the `process_all_students` function call:
    *   `anchor_radius`: Initial search radius in km (default: `5.0`).
    *   `expand_radius`: Multiplier for expanding the radius if not enough locations are found (default: `1.5`).

## Output

The system generates:
*   **`student_selections.csv`**: A CSV file containing the student list with 5 selected drugstore codes (`rank1` to `rank5`).
*   **Analysis Graphs**:
    *   `drugstore_analysis.png`: Geographic distribution and density.
    *   `sample_students_selection.png`: Visual examples of selections for specific students.
    *   `detailed_analysis.png`: Comprehensive statistics on distances and selection counts.

## Metrics

*   **Average Distance**: Typically 3-5 km between selected locations.
*   **Diversity**: The algorithm aims to utilize a large percentage of available drugstores (typically >70%) to prevent overcrowding at specific locations.

## License

This project is licensed under the MIT License.

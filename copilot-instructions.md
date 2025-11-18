````instructions
# Copilot Instructions for Bioacoustics Workspace

## Workspace Overview

Multi-project research workspace for **South African bird dialect classification** using deep learning, combining technical implementation with academic dissertation documentation.

**Research Context**: MSc(Eng) dissertation at UCT investigating hierarchical CNN architectures for dialect-level acoustic classification  
**Primary Technology**: BirdNET V2.4 dual-channel spectrograms, PyTorch CNNs, cross-platform deployment (Windows/macOS)  
**Data Scale**: 4,209 high-confidence segments across 11 South African species with 2-9 geographic dialects each

## Workspace Structure

```
Bioacoustics/
├── bird-dialect-cnn/              # Technical implementation (Python/PyTorch)
│   ├── .github/copilot-instructions.md   # Implementation-specific guidance
│   ├── hierarchical_dialect_classifier.py # Main production system
│   ├── streamlit_app.py                   # Interactive web UI
│   ├── src/models/                        # CNN architectures
│   ├── dataset/                           # 4,209 3-second WAV segments
│   └── experiments/                       # Training results
│
├── masters_dissertation_latex/    # Academic documentation (LaTeX)
│   ├── .github/copilot-instructions.md   # Documentation-specific guidance
│   ├── Main.tex                          # Dissertation root
│   ├── Chapters/                         # Core content
│   └── Bibliography/References.bib       # 996+ references
│
└── .venv/                         # Shared Python environment
```

## Critical Cross-Project Workflows

### 1. Implementation → Documentation Pipeline
When implementing new features in `bird-dialect-cnn/`, corresponding documentation updates are required in `masters_dissertation_latex/`:

```bash
# Example workflow
cd bird-dialect-cnn/
python hierarchical_dialect_classifier.py  # Generate results

# Extract metrics for dissertation
# - Training accuracy → Results chapter
# - Model architecture → Methodology chapter  
# - Performance plots → figures/ directory

cd ../masters_dissertation_latex/
# Update relevant .tex files with new results
```

### 2. Project-Specific Context Switching
**IMPORTANT**: Each subdirectory has its own `.github/copilot-instructions.md` with detailed project-specific guidance:

- **Working in `bird-dialect-cnn/`**: Consult `bird-dialect-cnn/.github/copilot-instructions.md` for:
  - BirdNET V2.4 technical specifications
  - Geographic cross-validation patterns
  - Cross-platform deployment (Windows/macOS)
  - Dataset structure and audio processing standards

- **Working in `masters_dissertation_latex/`**: Consult `masters_dissertation_latex/.github/copilot-instructions.md` for:
  - LaTeX structure and compilation
  - Academic writing conventions
  - Integration with codebase results
  - Bibliography management

### 3. Shared Development Environment
```bash
# Activate shared virtual environment (from workspace root)
source .venv/bin/activate              # macOS/Linux
# OR
.\.venv\Scripts\Activate.ps1          # Windows PowerShell

# Both projects use the same Python dependencies
pip install -r bird-dialect-cnn/requirements.txt
```

## Essential Workspace Patterns

### Directory Navigation
```bash
# Always work from appropriate project root
cd bird-dialect-cnn/          # For implementation work
python hierarchical_dialect_classifier.py

cd masters_dissertation_latex/ # For documentation work
pdflatex Main.tex
```

### File Path References
- **Implementation files**: Use relative paths from `bird-dialect-cnn/` root
  - Example: `dataset/high_confidence_segments_metadata.csv`
- **Documentation files**: Use relative paths from `masters_dissertation_latex/` root
  - Example: `Chapters/Methodology_Enhanced.tex`

### Git Workflow
```bash
# Each project maintains independent git history
cd bird-dialect-cnn/
git status                    # Implementation changes

cd ../masters_dissertation_latex/
git status                    # Documentation changes

# Workspace root is NOT a git repository
```

## Key Integration Points

### Results Extraction Pattern
```python
# In bird-dialect-cnn/hierarchical_dialect_classifier.py
# Extract metrics after training for dissertation

# Example: Species classifier results
species_accuracy = 62.3%      # → Results.tex, Table X
dialect_accuracy_range = 52.8-91.7%  # → Results.tex, Figure Y

# Save figures for LaTeX inclusion
import matplotlib.pyplot as plt
plt.savefig('../masters_dissertation_latex/Figures/confusion_matrix.pdf')
```

### Technical Terminology Consistency
- **Species Identification**: First stage of hierarchical classifier (11 species)
- **Dialect Classification**: Second stage, species-specific (2-9 dialects per species)
- **Geographic Clustering**: `geo_cluster` column prevents data leakage in cross-validation
- **BirdNET V2.4**: Dual-channel (2, 96, 511) mel spectrogram architecture
- **High-Confidence Segments**: 3-second WAV files with >0.8 BirdNET detection confidence

## Common Multi-Project Tasks

### Adding New Experimental Results
1. **Run experiments** in `bird-dialect-cnn/`
   ```bash
   cd bird-dialect-cnn/
   python hierarchical_dialect_classifier.py
   ```

2. **Extract metrics** from `experiments/checkpoints/*/logs/`
   - Training curves → `Results.tex`
   - Confusion matrices → `Figures/`
   - Performance tables → `Tables/`

3. **Update dissertation** in `masters_dissertation_latex/`
   ```latex
   % Chapters/Results.tex
   The hierarchical classifier achieved \textbf{62.3\%} species-level accuracy...
   ```

### Cross-Reference Documentation
- **Implementation docs**: `bird-dialect-cnn/docs/` (architecture, cleanup plans)
- **Academic context**: `masters_dissertation_latex/Chapters/` (research methodology)
- **Shared terminology**: Ensure consistency across both projects

### Testing Workflow
```bash
# Implementation testing
cd bird-dialect-cnn/
python fast_classifier_test.py        # Quick validation (~10-15 min)
python test_audio_file.py sample.wav  # Single file testing
streamlit run streamlit_app.py         # Interactive demo

# Documentation validation
cd masters_dissertation_latex/
pdflatex Main.tex                      # Check compilation
bibtex Main                            # Update references
```

## Platform-Specific Notes

### macOS (Current Platform)
- Terminal: zsh shell
- Python activation: `source .venv/bin/activate`
- GPU support: MPS (Apple Silicon) via PyTorch

### Windows (Cross-Platform Target)
- DataLoader settings: `num_workers=0`, `pin_memory=False`
- Python activation: `.\.venv\Scripts\Activate.ps1`
- CPU optimization: `os.environ['OMP_NUM_THREADS'] = '6'`

## Project-Specific Quick Reference

### bird-dialect-cnn/ Entry Points
```bash
hierarchical_dialect_classifier.py  # Complete training pipeline (2-4 hours)
streamlit_app.py                    # Interactive web UI
fast_classifier_test.py             # Quick validation (~10-15 min)
test_audio_file.py                  # Single file classification
```

### masters_dissertation_latex/ Entry Points
```latex
Main.tex                            # Root document
Chapters/Introduction_New.tex       # Current introduction
Chapters/Methodology_Enhanced.tex   # Technical methodology
Chapters/Results.tex                # Experimental results
```

## Critical Reminders

1. **Always check project-specific copilot-instructions.md** when working in subdirectories
2. **Geographic cross-validation**: Never use random splits - always use `geo_cluster` in `bird-dialect-cnn/`
3. **BirdNET specifications**: Exact dual-channel (2, 96, 511) format required for model compatibility
4. **Academic integrity**: Clearly mark Ostrich paper content vs. novel contributions in dissertation
5. **Cross-platform testing**: Validate on both Windows and macOS before deployment

## Getting Help

- **Implementation issues**: See `bird-dialect-cnn/.github/copilot-instructions.md`
- **Documentation issues**: See `masters_dissertation_latex/.github/copilot-instructions.md`
- **Architecture questions**: Check `bird-dialect-cnn/docs/CLEAN_STRUCTURE.md`
- **Research context**: Review `masters_dissertation_latex/Chapters/Introduction_New.tex`

This workspace enables efficient collaboration between technical implementation and academic documentation for South African bird dialect classification research.
````
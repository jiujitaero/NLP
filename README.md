# Voice recognition 
Implementation of various architectures that are available online and determine the model that best performs the "predefined goal" of the project.

## System requirements
* python = 3.9.xx
* torch = 

## Inference steps guideline 
```mermaid
graph TD
    A[Hydra Overrides + Config Dataclass] --> B{Config}
    B --> |Init| C[Model]
    B --> |Init| D[Trainer]
    C & D --> E[Set trainer]
    E --> |Optional| F[Change Transducer Decoding Strategy]
    F --> H[Load Manifest]
    E --> |Skip| H
    H --> I["model.transcribe(...)"]
    I --> J[Write output manifest]
    K[Ground Truth Manifest]
    J & K --> |Optional| L[Evaluate CER/WER]
```

During restoration of the model, you may pass the Trainer to the restore_from / from_pretrained call, or set it after the model has been initialized by using model.set_trainer(Trainer).

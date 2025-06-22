# VibeMatch Project Flowchart

This flowchart illustrates the complete pipeline of the VibeMatch movie recommendation system, integrating text-based emotion analysis and facial emotion recognition.

```mermaid
graph TD
    subgraph Data Acquisition & Preprocessing
        A[Start] --> B(Movie Overviews Dataset Input);
        A --> C(NRC Emotion Lexicon Input);
        A --> D(RAF-DB Facial Dataset Input);

        B --> B1{Clean & Tokenize Movie Overviews};
        C --> C1{Structure NRC Lexicon - Pivot and Omit Polarity};
        D --> D1{Resize & Normalize Facial Images};
    end

    subgraph Emotion Modeling
        subgraph Text-Based Emotion Profiling
            B1 --> T1[Search Word in NRC Lexicon];
            T1 -- Word NOT in NRC --> T2{Apply GloVe Word Embeddings};
            T1 -- Word IN NRC --> T3[Get Emotion Labels from NRC];
            T2 --> T4[Predict Emotion with Ridge Regression Model];
            T3 --> T4;
            T4 --> T5(10-D Emotion Vector per Word);
            T5 --> T6[Aggregate Word Vectors to Movie Vector];
            T6 --> Movie_E(Movie's Representative Emotion Vector);
        end

        subgraph Facial Emotion Recognition CNN
            D1 --> F1[CNN Model Architecture];
            F1 --> F2[Train CNN with RAF-DB Dataset];
            F2 --> F3[Apply Trained CNN to User Photo];
            F3 --> F4(7-Category Probability Distribution);
            F4 --> User_E(User's Dominant Facial Emotion Vector);
        end
    end

    subgraph Recommendation Generation & Output
        Movie_E & User_E --> R1{Calculate Cosine Similarity};
        R1 --> R2[Rank Movies by Similarity];
        R2 --> R3(Top 10 Recommended Movies);
        R3 --> Z[End];
    end

    %% Style Definitions
    style A fill:#FFDDC1,stroke:#FF8C00,stroke-width:2px;
    style Z fill:#FFDDC1,stroke:#FF8C00,stroke-width:2px;

    style B fill:#E0FFFF,stroke:#00CED1,stroke-width:2px;
    style C fill:#E0FFFF,stroke:#00CED1,stroke-width:2px;
    style D fill:#E0FFFF,stroke:#00CED1,stroke-width:2px;
    style Movie_E fill:#E0FFFF,stroke:#00CED1,stroke-width:2px;
    style User_E fill:#E0FFFF,stroke:#00CED1,stroke-width:2px;
    style R3 fill:#E0FFFF,stroke:#00CED1,stroke-width:2px;
    style T5 fill:#E0FFFF,stroke:#00CED1,stroke-width:2px;
    style F4 fill:#E0FFFF,stroke:#00CED1,stroke-width:2px;

    style B1 fill:#F5F5DC,stroke:#DAA520,stroke-width:2px;
    style C1 fill:#F5F5DC,stroke:#DAA520,stroke-width:2px;
    style D1 fill:#F5F5DC,stroke:#DAA520,stroke-width:2px;

    style T1 fill:#ADD8E6,stroke:#4682B4,stroke-width:2px;
    style T2 fill:#ADD8E6,stroke:#4682B4,stroke-width:2px;
    style T3 fill:#ADD8E6,stroke:#4682B4,stroke-width:2px;
    style T4 fill:#ADD8E6,stroke:#4682B4,stroke-width:2px;
    style T6 fill:#ADD8E6,stroke:#4682B4,stroke-width:2px;

    style F1 fill:#ADD8E6,stroke:#4682B4,stroke-width:2px;
    style F2 fill:#ADD8E6,stroke:#4682B4,stroke-width:2px;
    style F3 fill:#ADD8E6,stroke:#4682B4,stroke-width:2px;

    style R1 fill:#D3D3D3,stroke:#808080,stroke-width:2px;
    style R2 fill:#D3D3D3,stroke:#808080,stroke-width:2px;

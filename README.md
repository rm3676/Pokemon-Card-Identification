# Pokemon-Card-Identification
Pokémon Card Identification App - A deep learning–powered application that identifies Pokémon Trading Card Game (TCG) cards from images. Using a fine-tuned ResNet model, the app can recognize thousands of cards, including rare promos and subtle set variations, and display full card details like name, set, rarity, and type.

# Features
Image Upload & Identification: Upload a Pokémon card image, and the app predicts the exact card.

High Accuracy Model: Achieved 93.62% training accuracy using ResNet-18.

Data Integration: Combines card images with metadata (set, rarity, artist, HP, etc.) for complete results.

FastAPI Backend: Provides an API endpoint (/identify_card) to process images and return predictions in JSON.

Interactive Docs: Swagger and ReDoc available for testing API calls.

# How It Works

1.Data Preparation: Collected card images and metadata (Kaggle datasets). Cleaned by removing duplicates and corrupt files.

2.Dataset Standardization: Converted all images to RGB, resized to 224×224 pixels, and stored as JPEG.

3.Data Integration: Built a manifest linking images to card IDs and merged with TCG metadata. Created numeric labels (id2idx, idx2id).

4.Model Training:

Fine-tuned a pretrained ResNet-18.

Replaced final layer with number of unique cards.

Applied strong augmentation (flips, rotations, color jitter).

Trained for 10 epochs → reached 93.62% accuracy.

5.Prediction & Inference: User uploads a card → model predicts ID → details (set, rarity, type, etc.) are retrieved and displayed.

# Tech Stack
Python 3.10+

PyTorch (ResNet model training)

FastAPI (backend API)

Pandas / NumPy (data handling)

Torchvision (image preprocessing & augmentation)

# Project Structure
backend/

│── app/

│   └── main.py              # FastAPI app entry point

│── data/

│   └── pokemon-manifest.csv # Manifest linking images + metadata

│── model/

│   └── pokemon_card_model.pth # Trained model weights

│── label/

│   └── idx2id.json          # Mapping file for predictions

│── notebook/

│   └── core-backend-notebook.ipynb # Training & exploration

│── requirements.txt

│── README.md

# Credits / Data Sources

- **Pokémon TCG Card Images Dataset**
  - Source: [Kaggle - pokemon-cards.csv by priyamchoksi](https://www.kaggle.com/datasets/priyamchoksi/pokemon-cards)
  - Author: priyamchoksi
  - License: See dataset page for terms

- **Pokémon Card Metadata Dataset**
  - Source: [Kaggle - pokemon-tcg-data-master 1999-2023.csv by adampq](https://www.kaggle.com/datasets/adampq/pokemon-tcg-all-cards-1999-2023)
  - Author: adampq
  - License: See dataset page for terms

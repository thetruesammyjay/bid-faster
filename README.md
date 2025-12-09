# Bid Faster - Automated Procurement Evaluation System

An AI-powered procurement automation platform that streamlines vendor verification, document processing, and bid evaluation.

## Overview

Bid Faster automates the entire bid evaluation process by intelligently processing vendor documents, validating certifications, and scoring submissions based on customizable evaluation templates. The system handles multiple document formats and generates comprehensive reports to help procurement teams make faster, more accurate decisions.

## Key Features

- **Multi-Format Document Processing**: Handles PDF, Word, Excel, Images, Scanned Documents, and Text files
- **Automated Certification Verification**: Validates TIN certificates, OEM authorizations, DPR/NUPRC permits, tax clearance, and insurance certificates
- **Template-Based Scoring**: Extracts evaluation criteria from templates and applies them consistently across all bids
- **Batch Processing**: Upload and process multiple bidder submissions simultaneously
- **Intelligent Ranking**: Automatically identifies top bidders with detailed score justifications
- **Dual Report Generation**: Produces both detailed evaluation reports and executive summaries
- **Export Flexibility**: Outputs available in PDF and Excel formats

## Technology Stack

- **AI/ML Framework**: [Your chosen framework - e.g., LangChain, Hugging Face]
- **OCR Engine**: Tesseract / Cloud Vision API
- **Document Processing**: PyPDF2, python-docx, openpyxl, Pillow
- **Backend**: Python with FastAPI/Flask
- **Database**: PostgreSQL / MongoDB
- **Queue System**: Celery with Redis
- **Storage**: AWS S3 / Google Cloud Storage

## Installation

### Prerequisites

- Python 3.9+
- PostgreSQL 13+ (or MongoDB 5+)
- Redis 6+
- Node.js 16+ (for frontend, if applicable)

### Setup

```bash
# Clone the repository
git clone https://github.com/thetruesammyjay/bid-faster.git
cd bid-faster

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Run database migrations
python manage.py migrate

# Start the application
python manage.py runserver
```

## Configuration

Create a `.env` file in the root directory:

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/bidfaster

# Redis
REDIS_URL=redis://localhost:6379/0

# Cloud Storage
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key
AWS_BUCKET_NAME=bid-faster-documents

# AI/ML
OPENAI_API_KEY=your_api_key  # If using OpenAI
MODEL_PATH=./models/evaluation_model

# Application
SECRET_KEY=your_secret_key
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1
```

## Usage

### 1. Upload Evaluation Template

```python
from bidfaster import TemplateProcessor

processor = TemplateProcessor()
template = processor.upload_template("evaluation_criteria.xlsx")
```

### 2. Submit Bidder Documents

```python
from bidfaster import BidProcessor

bid_processor = BidProcessor(template_id=template.id)
result = bid_processor.process_bid(
    vendor_name="ABC Corporation",
    documents=[
        "tin_certificate.pdf",
        "oem_authorization.pdf",
        "technical_proposal.docx"
    ]
)
```

### 3. Generate Reports

```python
from bidfaster import ReportGenerator

generator = ReportGenerator()

# Detailed report
detailed = generator.generate_detailed_report(
    project_id="PRJ-2024-001",
    format="pdf"
)

# Summary report
summary = generator.generate_summary_report(
    project_id="PRJ-2024-001",
    top_n=5,
    format="excel"
)
```

## API Endpoints

### Document Upload
```
POST /api/v1/documents/upload
Content-Type: multipart/form-data
```

### Process Evaluation
```
POST /api/v1/evaluations/process
{
  "project_id": "string",
  "template_id": "string",
  "vendor_submissions": []
}
```

### Get Results
```
GET /api/v1/evaluations/{evaluation_id}/results
Query params: format=[pdf|excel], type=[detailed|summary]
```

## Document Types Supported

### Vendor Certifications
- TIN (Tax Identification Number) Certificate
- OEM (Original Equipment Manufacturer) Authorization
- DPR/NUPRC Permits
- Tax Clearance Certificate
- Insurance Certificates
- Company Registration Documents

### Bid Submissions
- Technical Proposals
- Financial Proposals
- Company Profiles
- Past Performance Records
- Quality Certifications (ISO, etc.)

## Scoring System

The evaluation engine processes templates to extract:
- **Mandatory Requirements**: Pass/Fail criteria
- **Technical Criteria**: Weighted scoring based on specifications
- **Financial Criteria**: Price evaluation and comparison
- **Experience Criteria**: Past performance and references
- **Compliance Criteria**: Certification validity and completeness

## Output Reports

### Detailed Report Includes:
- Complete vendor information
- Document-by-document analysis
- Certification validation status
- Item-by-item scoring breakdown
- Compliance checklist
- Risk flags and warnings

### Summary Report Includes:
- Top bidder ranking
- Final scores with weights applied
- Key strengths per bidder
- Score justification notes
- Recommended award decision

## Development

### Running Tests
```bash
pytest tests/
```

### Code Quality
```bash
# Linting
flake8 bidfaster/

# Type checking
mypy bidfaster/

# Format code
black bidfaster/
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For issues, questions, or contributions:
- GitHub Issues: https://github.com/thetruesammyjay/bid-faster/issues
- Email: support@bidfaster.com
- Documentation: https://docs.bidfaster.com

## Roadmap

- [ ] Multi-language support for document processing
- [ ] Real-time collaboration features
- [ ] Advanced fraud detection algorithms
- [ ] Integration with major ERP systems
- [ ] Mobile application for on-the-go evaluations
- [ ] Blockchain-based audit trail

## Acknowledgments

- Document processing powered by [OCR Engine]
- AI evaluation engine built with [ML Framework]
- Nigerian procurement standards compliance

---

**Version**: 1.0.0  
**Last Updated**: December 2024  
**Maintained by**: The True Sammy Jay

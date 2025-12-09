# Bid Faster - Project File Structure

```
bid-faster/
├── README.md
├── LICENSE
├── .gitignore
├── .env.example
├── requirements.txt
├── setup.py
├── Dockerfile
├── docker-compose.yml
├── pytest.ini
├── .flake8
├── mypy.ini
│
├── docs/
│   ├── api/
│   │   ├── endpoints.md
│   │   ├── authentication.md
│   │   └── webhooks.md
│   ├── guides/
│   │   ├── getting-started.md
│   │   ├── template-creation.md
│   │   ├── document-upload.md
│   │   └── report-generation.md
│   ├── architecture/
│   │   ├── system-design.md
│   │   ├── data-flow.md
│   │   └── ml-pipeline.md
│   └── deployment/
│       ├── aws-deployment.md
│       ├── gcp-deployment.md
│       └── docker-deployment.md
│
├── bidfaster/
│   ├── __init__.py
│   ├── config.py
│   ├── constants.py
│   ├── exceptions.py
│   │
│   ├── api/
│   │   ├── __init__.py
│   │   ├── main.py
│   │   ├── dependencies.py
│   │   ├── routes/
│   │   │   ├── __init__.py
│   │   │   ├── documents.py
│   │   │   ├── evaluations.py
│   │   │   ├── templates.py
│   │   │   ├── vendors.py
│   │   │   ├── reports.py
│   │   │   └── auth.py
│   │   └── middleware/
│   │       ├── __init__.py
│   │       ├── auth.py
│   │       ├── logging.py
│   │       └── rate_limiting.py
│   │
│   ├── core/
│   │   ├── __init__.py
│   │   ├── document_processor.py
│   │   ├── template_parser.py
│   │   ├── evaluation_engine.py
│   │   ├── scoring_system.py
│   │   ├── certification_validator.py
│   │   └── report_generator.py
│   │
│   ├── ml/
│   │   ├── __init__.py
│   │   ├── models/
│   │   │   ├── __init__.py
│   │   │   ├── document_classifier.py
│   │   │   ├── text_extractor.py
│   │   │   ├── entity_recognizer.py
│   │   │   └── fraud_detector.py
│   │   ├── preprocessing/
│   │   │   ├── __init__.py
│   │   │   ├── image_processor.py
│   │   │   ├── text_cleaner.py
│   │   │   └── feature_extractor.py
│   │   └── training/
│   │       ├── __init__.py
│   │       ├── train_classifier.py
│   │       ├── train_ner.py
│   │       └── evaluate_model.py
│   │
│   ├── processors/
│   │   ├── __init__.py
│   │   ├── base_processor.py
│   │   ├── pdf_processor.py
│   │   ├── word_processor.py
│   │   ├── excel_processor.py
│   │   ├── image_processor.py
│   │   ├── scanned_doc_processor.py
│   │   └── text_processor.py
│   │
│   ├── validators/
│   │   ├── __init__.py
│   │   ├── base_validator.py
│   │   ├── tin_validator.py
│   │   ├── oem_validator.py
│   │   ├── permit_validator.py
│   │   ├── tax_clearance_validator.py
│   │   └── insurance_validator.py
│   │
│   ├── database/
│   │   ├── __init__.py
│   │   ├── base.py
│   │   ├── models/
│   │   │   ├── __init__.py
│   │   │   ├── project.py
│   │   │   ├── vendor.py
│   │   │   ├── document.py
│   │   │   ├── template.py
│   │   │   ├── evaluation.py
│   │   │   ├── certification.py
│   │   │   └── user.py
│   │   ├── repositories/
│   │   │   ├── __init__.py
│   │   │   ├── project_repo.py
│   │   │   ├── vendor_repo.py
│   │   │   ├── document_repo.py
│   │   │   └── evaluation_repo.py
│   │   └── migrations/
│   │       └── versions/
│   │
│   ├── storage/
│   │   ├── __init__.py
│   │   ├── base_storage.py
│   │   ├── s3_storage.py
│   │   ├── gcs_storage.py
│   │   └── local_storage.py
│   │
│   ├── services/
│   │   ├── __init__.py
│   │   ├── document_service.py
│   │   ├── evaluation_service.py
│   │   ├── vendor_service.py
│   │   ├── template_service.py
│   │   ├── notification_service.py
│   │   └── export_service.py
│   │
│   ├── utils/
│   │   ├── __init__.py
│   │   ├── file_utils.py
│   │   ├── date_utils.py
│   │   ├── text_utils.py
│   │   ├── validation_utils.py
│   │   ├── logger.py
│   │   └── helpers.py
│   │
│   └── schemas/
│       ├── __init__.py
│       ├── document.py
│       ├── evaluation.py
│       ├── vendor.py
│       ├── template.py
│       ├── report.py
│       └── user.py
│
├── tests/
│   ├── __init__.py
│   ├── conftest.py
│   ├── unit/
│   │   ├── __init__.py
│   │   ├── test_document_processor.py
│   │   ├── test_template_parser.py
│   │   ├── test_evaluation_engine.py
│   │   ├── test_validators.py
│   │   └── test_scoring_system.py
│   ├── integration/
│   │   ├── __init__.py
│   │   ├── test_api_endpoints.py
│   │   ├── test_document_pipeline.py
│   │   ├── test_evaluation_flow.py
│   │   └── test_report_generation.py
│   ├── e2e/
│   │   ├── __init__.py
│   │   └── test_complete_workflow.py
│   └── fixtures/
│       ├── documents/
│       │   ├── sample_tin.pdf
│       │   ├── sample_proposal.docx
│       │   └── sample_scanned.jpg
│       ├── templates/
│       │   └── evaluation_template.xlsx
│       └── data/
│           └── test_data.json
│
├── scripts/
│   ├── setup_db.py
│   ├── seed_data.py
│   ├── train_models.py
│   ├── backup_database.sh
│   ├── deploy.sh
│   └── performance_test.py
│
├── models/
│   ├── document_classifier/
│   │   ├── model.pkl
│   │   ├── tokenizer.pkl
│   │   └── config.json
│   ├── ner_model/
│   │   ├── model.pkl
│   │   └── label_encoder.pkl
│   └── fraud_detector/
│       ├── model.pkl
│       └── scaler.pkl
│
├── templates/
│   ├── email/
│   │   ├── evaluation_complete.html
│   │   ├── vendor_notification.html
│   │   └── error_notification.html
│   └── reports/
│       ├── detailed_report_template.html
│       ├── summary_report_template.html
│       └── styles.css
│
├── static/
│   ├── css/
│   ├── js/
│   └── images/
│
├── data/
│   ├── raw/
│   ├── processed/
│   ├── training/
│   └── exports/
│
├── logs/
│   ├── app.log
│   ├── error.log
│   └── access.log
│
└── config/
    ├── development.py
    ├── production.py
    ├── testing.py
    └── logging.yaml
```

## Key Directory Descriptions

### `/bidfaster/core/`
Core business logic including document processing, template parsing, evaluation engine, and report generation.

### `/bidfaster/ml/`
Machine learning models for document classification, text extraction, entity recognition, and fraud detection.

### `/bidfaster/processors/`
Specialized processors for different document formats (PDF, Word, Excel, Images, Scanned documents).

### `/bidfaster/validators/`
Certification validators for TIN, OEM, permits, tax clearance, and insurance documents.

### `/bidfaster/database/`
Database models, repositories, and migrations for data persistence.

### `/bidfaster/api/`
RESTful API implementation with routes, middleware, and dependencies.

### `/bidfaster/services/`
Business service layer that orchestrates core functionality.

### `/tests/`
Comprehensive test suite including unit, integration, and end-to-end tests.

### `/models/`
Pre-trained ML models and their configurations.

### `/scripts/`
Utility scripts for deployment, database management, and training.

### `/templates/`
HTML templates for reports and email notifications.

## Key Files

- **requirements.txt**: Python dependencies
- **setup.py**: Package installation configuration
- **docker-compose.yml**: Container orchestration
- **pytest.ini**: Test configuration
- **.env.example**: Environment variables template
- **config.py**: Application configuration management

## Next Steps

1. Initialize the project structure
2. Set up virtual environment and install dependencies
3. Configure database and storage
4. Implement core processors and validators
5. Build ML models for document classification
6. Create API endpoints
7. Write comprehensive tests
8. Deploy to production environment

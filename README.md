# SkillSync Project

![Django](https://img.shields.io/badge/Django-4.1.0-brightgreen.svg)
![Python](https://img.shields.io/badge/Python-3.11.0-blue.svg)
![License](https://img.shields.io/badge/License-MIT-orange.svg)

SkillSync is a Django-based project for managing courses and modules. It provides a flexible system for organizing educational content.

## Table of Contents

- [Models](#models)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Models

### Subject

The `Subject` model represents the subjects or topics of your courses.

- `title` (CharField): The title of the subject.
- `slug` (SlugField): A unique slug for the subject.

### Course

The `Course` model represents individual courses.

- `owner` (ForeignKey to User): The owner of the course.
- `subject` (ForeignKey to Subject): The subject to which the course belongs.
- `title` (CharField): The title of the course.
- `slug` (SlugField): A unique slug for the course.
- `overview` (TextField): An overview of the course.
- `created` (DateTimeField): The creation date of the course.

### Module

The `Module` model represents modules within a course.

- `course` (ForeignKey to Course): The course to which the module belongs.
- `title` (CharField): The title of the module.
- `description` (TextField, optional): A description of the module.
- `order` (OrderField, optional): The order of the module within the course.

### Content

The `Content` model represents the content of a module.

- `module` (ForeignKey to Module): The module to which the content belongs.
- `content_type` (ForeignKey to ContentType): The type of content (text, video, image, file).
- `object_id` (PositiveIntegerField): The ID of the related content item.
- `item` (GenericForeignKey): The related content item.
- `order` (OrderField, optional): The order of the content within the course.

### ItemBase (Abstract Model)

The `ItemBase` model is an abstract base model for content items.

- `owner` (ForeignKey to User): The owner of the content item.
- `title` (CharField): The title of the content item.
- `created` (DateTimeField): The creation date of the content item.
- `updated` (DateTimeField): The last updated date of the content item.

#### Content Item Models

1. **Text**: Represents text content.
2. **File**: Represents file content.
3. **Image**: Represents image content.
4. **Video**: Represents video content.

## Installation

1. Clone the repository: `git clone https://github.com/yourusername/SkillSync.git`
2. Create a virtual environment: `python -m venv venv`
3. Activate the virtual environment:
   - On Windows: `venv\Scripts\activate`
   - On macOS and Linux: `source venv/bin/activate`
4. Install dependencies: `pip install -r requirements.txt`
5. Run migrations: `python manage.py migrate`
6. Create a superuser: `python manage.py createsuperuser`
7. Start the development server: `python manage.py runserver`

## Usage

1. Log in to the admin panel using your superuser credentials: `http://localhost:8000/admin/`
2. Create subjects, courses, modules, and content items to organize your educational content.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

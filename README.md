Portfolio App
---

A Django application for managing portfolios, resumes and other information centered websites.

Provides RESTful interfaces for 
- Projects
- Journals
- Bios
- Contact pages

Projects
---

Projects are a domain to showcase your work.
They have a title, date, description, display photo, tags and most importantly a report,
which has headings, subheadings, paragraphs and yes, photos.

#### Objectives
- Streamline showcasing your projects

@startuml

package ProjectDomain <<Cloud>> {

  class Project {
    title: str
    date: obj
    description: str
    photo: str
    tags: list
    updateData()
    editReport()
  }

  class Report {
    editItems()
  }

  class Item {
    type
    section
    index
    content
    updateData()
  }

  Project ||-|| Report
  Report ||-o{ Item

}
@enduml

Journals
---

Journals are a domain to document your process.
They are essentially blogs.
They have entries which have a date, author, title and body.

#### Objectives
- Streamline documenting your process

@startuml

package JournalDomain <<Cloud>> {
  class Entry {
    author
    title
    date
    body
    updateData()
  }
}

@enduml

Bios
---

Bios are a domain to introduce yourself.
Add a describing text about yourself along with your resume.
Spice it up with a headshot and some hyperlinks to your social media.

#### Objectives
- Streamline adding and updating your resume.

@startuml

package BiosDomain <<Cloud>> {

  class Person {
    name: str
    bio: str
    updateData()
    editExperience()
    editEducation()
    editSkills()
  }
  class Experience {
    company: str
    title: str
    description: str
    period: obj
    updateData()
  }
  class Education {
    school: str
    degree: str
    description: str
    year: int
    updateData()
  }
  class Skills {
    category: str
    items: list
    updateData()
  }

  Person ||--o{ Experience
  Person ||--o{ Skills
  Person ||--o{ Education

}
@enduml

Contact
---

Contact is a domain to.. you guessed it: contact.

#### Objectives
- Set up a pipeline from consuming a POST request to delivering data via email.

@startuml

package ContactDomain <<Cloud>> {
  
  class Request {
    name: str
    email: str
    body: str
  }
}

@enduml

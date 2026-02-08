# Semantic Resume

This is a LaTeX template for a resume that with custom environments/commands to
make modifications easier.

While resume templates are widely available, this template is designed to be
easily parseable and modifiable for the user _writing_ the resume, in addition
to being ATS-friendly. Additionally, the formatted output is optimised for my
own aesthetic preferences.

Based on [Jake's Resume](https://github.com/jakegut/resume) template for the
baseline layout.

## How to compile

The template can be compiled using `pdflatex`, or any other LaTeX compiler.

```bash
pdflatex resume.tex
```

## What features does this have?

This template uses semantic commands to make the source code readable and
extensible.

### Experiences & positions
The `resumeExperience` environment is used for any section involving
organizations, roles, and dates (Experience, Extracurriculars, Projects, etc.).

#### Custom commands
- `\experienceOrganisationLocation{Name}{Location}`: Defines the top-level
entity (company, school, club, etc.), with the name bolded. The name and
location will be left-aligned and right-aligned respectively.
- `\experiencePositionDate{Title}{Date}`: Defines the specific role and
timeline, with the date and title italicised. The title and date will be
left-aligned and right-aligned respectively.
- `\achievement{Description}`: Defines a bullet point. The text will be slightly
lighter than the default text colour.

#### Modularity
Experiences can be modular. You can list multiple positions under a single
organization by simply adding more `\experiencePositionDate` blocks under the
same `\experienceOrganisationLocation`.

*Example:*
```latex
\begin{resumeExperience}
  \experienceOrganisationLocation
    {Company Name}
    {Location}

    % Second position at the company (promotion?)
    \experiencePositionDate
      {Role Title 2}
      {Jan 2021 -- Present}
    \begin{experienceAchievementList}
      \achievement{Did even cooler stuff.}
    \end{experienceAchievementList}

    \vspace{-3pt} % suggested for vertical spacing between positions
  
    % First position at the company
    \experiencePositionDate
      {Role Title 1}
      {Jan 2020 -- Dec 2020}
    \begin{experienceAchievementList}
      \achievement{Did cool stuff.}
    \end{experienceAchievementList}

\end{resumeExperience}
```

### Skills & Lists
The `categoryList` environment is used for simple two-column formatting, perfect
for listing awards or skills. The first argument is the category name, and the
second is the list of items, which will be right-aligned.

*Example:*
```latex
\begin{categoryList}
  \categoryItem{Languages:}{Python, Java, C++}
  \categoryItem{Tools:}{Docker, AWS, Git}
\end{categoryList}
```

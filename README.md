# Semantic Resume

This is a LaTeX template for a resume that with custom environments/commands to
make modifications easier.

While resume templates are widely available, this template is designed to be
easily parseable and modifiable for the user _writing_ the resume, in addition
to being ATS-friendly. Additionally, the formatted output is optimised for my
own aesthetic preferences.

Based on [Jake's Resume](https://github.com/jakegut/resume) template for the
baseline layout.

## Usage

This template uses semantic commands and environments to make the source code readable and extensible.

### Environments & commands

The template is built around the `resumeExperience` environment. Everything inside this environment is a list element (`\item`), which ensures consistent vertical spacing and alignment across different sections.

#### Structuring sections

The `resumeExperience` is main wrapper environment for all content sections (Education, Skills, Experience, Projects). It initializes the main list structure. Every section should have its own `resumeExperience` environment for structuring its contents.

The sections themselves can be created using the standard `\section` command.

#### Content blocks
Since they operate within `resumeExperience`, the following commands act as formatted list items:

- `\experienceOrganisationLocation{Name}{Location}`: Bolded name (left) and location (right).
- `\experiencePositionDate{Title}{Date}`: Italicised title (left) and date (right).
- `\experienceProjectDate{Project name}{Date}`: Bolded project (left) and date (right).
- `\categoryList{Category}{Content}`: Two-column row for skills, awards, or any other in-lined list. Labels are bolded.
- `experienceAchievementList`: A nested environment used to list tailored achievements/bullet points. It creates a sub-list (which is itself an item) under the current experience environment.
  - `\achievement{Description}`: Individual bullet points within the achievement list.

### Examples

#### Experience / projects
Experiences are modular. You can list multiple positions under a single organization or mix and match blocks.

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

  % First position at the company
  \experiencePositionDate
    {Role Title 1}
    {Jan 2020 -- Dec 2020}
  \begin{experienceAchievementList}
    \achievement{Did cool stuff.}
  \end{experienceAchievementList}

\end{resumeExperience}
```

#### In-lined lists
The `\categoryList` command creates a clean tabular look for skills, but it must be used inside `resumeExperience`.

```latex
\begin{resumeExperience}
  \categoryList{Languages:}{Python, Java, C++}
  \categoryList{Tools:}{Docker, AWS, Git}
\end{resumeExperience}
```

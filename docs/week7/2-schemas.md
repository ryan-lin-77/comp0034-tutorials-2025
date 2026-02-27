# 2. Create schemas

## Pydantic or SQLModel?

If you remember, SQLModel uses SQLAlchemy and Pydantic under the covers. If you are using
SQLModel you can use this for schemas and models.

You do not have to use SQLModel for the coursework. You may wish to use SQLAlchemy, particularly
if you plan to work with databases beyond this course as it is widely used so you may prefer to
learn the direct syntax now.

If you choose to use SQLAlchemy then use this for the model classes, and Pydantic for the schemas.
You could also search PyPi for packages that support generation of Pydantic schemas from
sqlalchemy models.

There will be an example of Pydantic schemas in the tutor solutions for this week. You could also
use Copilot or other to generate schemas from the models e.g.

> Generate Pydantic Base, Create, Read and Update schemas for the Games, Team, Country, Disability,
> Host, Question, and Response classes in models.py.
> Base defines the core fields, others inherit from that.
> In the Read models, use `model_config = ConfigDict(from_attributes=True)`

Note that in Read models, Copilot seems to use `class Config:  from_attributes = True` whereas the
documentation suggests `model_config = ConfigDict(from_attributes=True)` is now preferred.

## Create the schemas using SQLModel

For each of the existing models, create a set of models and schemas:

- `BaseSomething(SQLModel)`: base schema with common attributes for all schemas
- `Something(BaseSomething, table=True)`: the database table model (if you prefer leave these as is,
  then don't inherit from BaseSomething, leave this as SQLModel)
- `SomethingCreate(BaseSomething)`: schema for creating new something
- `SomethingRead(BaseSomething)`: response schema
- `SomethingUpdate(SQLModel)`: schema for partial updates making all fields optional

Table 2 in the first activity gives more explanation of the differences.

Create schemas for the Paralympics API in `paralympics.models.schemas.py`.

[Next activity](3-get-routes.md)

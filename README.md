```#!/usr/bin/env python3

from faker import Faker
import random
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker

from models import Game

faker = Faker()

if **name** == "**main**":
engine = create_engine("sqlite:///seed_db.db")

    Session = sessionmaker(bind=engine)
    session = Session()
    # to clear the database of the old existing data
    session.query(Game).delete()
    session.commit()
    # # create the game instances for other programmers`

    # botw = Game(
    #     title="Breath of the Wild", platform="Switch", genre="Adventure", price=60
    # )
    # ffvii = Game(
    #     title="Final Fantasy VII", platform="Playstation", genre="RPG", price=30
    # )
    # mk8 = Game(title="Mario Kart 8", platform="Switch", genre="Racing", price=50)
    # ccs = Game(title="Candy Crush Saga", platform="Mobile", genre="Puzzle", price=0)

    # session.add_all([botw, ffvii, mk8, ccs])
    # session.commit()

    # --------------------- delete all the records =====================
    records = (session.query(Game).all())
    # for record in records:
    #     session.delete(record)
    # session.commit()
    # print(session.query(Game).all())




    # print(session.query(Game).count())
    # print(session.query(Game)[-1])

    # -------- F  A K E R ----------------
    games = [
        Game(
            title = faker.name(),
            genre = faker.word(),
            platform =faker.word(),
            price = random.randint(0,50)
        )
        for i in range(50)
    ]

    # print(games)
    session.add_all(games)
    session.commit()
```

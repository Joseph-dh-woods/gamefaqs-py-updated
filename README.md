GameFaqsPY
========

GameFaqsPY is a python package useful to retrieve and manage game data from the GameFAQS website.  The package is written in pure python and provides the following game information:

* Title
* Description
* Platform
* Release Date
* Companies
* ESRB Rating
* Metascore
* User Rating (/5)
* Difficulty
* Length (hr)
* Unlockables
* Cheat Codes

Installation
------------

GameFaqsPY is conveniently available via pip:

    pip install gamefaqs-py

or installable via ``git clone`` and ``setup.py``

    git clone https://github.com/ryantonini/gamefaqs-py.git
    sudo python setup.py install

Since version 0.2.5, the application has supported database access.  The database access system runs queries significantly faster than the `http` alternative.  To use the database system, run the following script upon installation:

    python /path/to/run_load.py

The script will create a SQLite database file in the current working directory containing data loaded from http://www.gamefaqs.com/.

NOTE: Version 0.2.8 features database game support from all the popular platforms.

Usage
-----

A code example:

```python
    from gamefaqs import access
    
    # using the http access system (default)
    gf_access = access.GameFaqs()
    
    first_game = gf_access.search_game("Metal Gear Solid: Peace Walker")[0]
    first_game.summary()
    
    gf_access.update(first_game, info=["general", "rating"])
    print first_game(["esrb"])
    print first_game(["metascore"])
    
    first_company = gf_access.search_company("Microsoft")[0]
    first_company.summary()
    
    gf_access.update(first_company)
    print(first_company["name"])
    print(first_company["games"])
```

License
-------

GNU General Public License Version 3.  See LICENSE for more details.
    


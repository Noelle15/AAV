'''
On souhaite développer une classe Dictionnaire capable de stocker des mots, définis sur l’alphabet à 26 lettres
allant de a à z. La première idée envisagée est généralement de développer une liste triée de ces mots, par ordre
lexicographique. Toutefois, afin de tirer parti de la redondance des mots, il est alternativement possible de les
stocker dans un arbre général, ou plus précisément dans une forêt d’arbres généraux.
Concrètement, cette forêt se compose d’une structure linéaire de 26 éléments (au plus) allant de la lettre a à
la lettre z. Chaque élément / lettre est lié(e) à un arbre général, qui contient tous les mots débutant par cette
lettre. Cet arbre code plus précisément les suffixes de ces mots, amputés de cette première lettre. Pour ce faire, il
contient lui-même une liste de 26 éléments (au plus) allant de la lettre a à la lettre z, etc.
À titre d’exemple, les mots bassin, bas et bidon, sont « stockés » dans l’élément b de la forêt. La lettre initiale
b de ces trois mots y est factorisée, et les sous-mots assin, as et idon sont ensuite codés dans un arbre général,
contenant une liste qui répartit les sous-mots assin, as dans l’élément de la lettre a, et idon dans celui de la lettre
i, et ainsi de suite. On remarque, au passage, qu’un mot (par exemple bas) peut être un préfixe d’un autre (par
exemple bassin) : ce point aura son importance par la suite.
'''

class Letter:
    def __init__(self, l):
        self.l = l;
        self.list = [0]*26

    def add_word(self, word):
        word = word.lower()
        if len(word)!=0:
            objet = Letter(word[0])
            self.list.insert((ord(word[0])-97),objet)
            objet.add_word(word[1:])

    def search_word(self, word):
        word = word.lower()
        if len(word) != 0:    
            if word[0] == self.l:
                self.l.search_word(word[1:])
            elif self.list[ord(word[0])-97] != 0:
                self.list[ord(word[0])-97].search_word(word[1:])
            else:
                return False
        
        return True

    def show(self, prefix):
        pass  # TODO

    def get_depth(self):
        
        pass  # TODO

    def get_size(self):
        pass  # TODO

    def delete_word(self):
        pass  # TODO
        

           


def search(root, word):
    print("search for %s : %s" % (word, root.search_word(word)))


def test_minimal():
    root = Letter('')
    root.add_word('Sophie')
    assert root.search_word('sophie')
   # assert root.get_depth() == len('sophie')
   # assert root.get_size() == 1


test_minimal()

def setup_root():
    root = Letter('')
    root.add_word('Batman')
    root.add_word('Batman')  # Should do nothing
    root.add_word('Batgirl')
    root.add_word('Batwoman')
    root.add_word('Batcow')
    root.add_word('Nightwing')
    root.add_word('Robin')
    root.add_word('Gordon')
    root.add_word('Alfred')
    root.add_word('Oracle')
    root.add_word('Catwoman')
    root.add_word('Harleyquinn')
    root.add_word('Ivy')
    root.add_word('Joker')
    root.add_word('Scarecrow')
    root.add_word('Pingouin')
    root.add_word('Owls')
    root.add_word('Twoface')
    root.add_word('Riddler')
    root.add_word('Bane')
    root.add_word('Rasalghul')
    root.add_word('Taliaalghul')
    root.add_word('Killercroc')
    root.add_word('Deadshot')
    root.add_word('Deadstroke')
    root.add_word('Manbat')
    return root


def test_search():
    root = setup_root()
    assert root.search_word('batman')
    assert not root.search_word('sophie')
    assert not root.search_word('bat')
    assert not root.search_word('')
    assert root.search_word('manbat')


def test_size():
    root = setup_root()
    assert root.get_depth() == len('Taliaalghul')
    assert root.get_size() == 25


def test_delete():
    root = setup_root()

    old_size = root.get_size()
    root.delete_word('batman')
    assert root.search_word('batgirl')
    assert old_size == root.get_size() - 1


def test_big():
    data_shuffled = get_data_shuffled()
    root = Letter('')

    for word in data_shuffled:
        root.add_word(word)

    assert root.search_word('pikachu')
    assert not root.search_word('sophie')
    assert root.get_depth() == 13
    assert root.get_size() == 379

def test_avg():
    data_shuffled = get_data_shuffled()
    root = Letter('')

    for word in data_shuffled:
        root.add_word(word)

    assert root.search_word('pikachu')
    assert not root.search_word('sophie')
    assert root.get_depth() == 13
    assert root.get_size() == 379


def get_data():
    data = ['Abra', 'Absol', 'Aerodactyl', 'Aggron', 'Aipom', 'Alakazam', 'Altaria', 'Amaldo', 'Ampharos', 'Anorith',
        'Arbok', 'Arcanine', 'Ariados', 'Aron', 'Articuno', 'Azumarill', 'Azurill',
        'Bagon', 'Baltoy', 'Banette', 'Barboach', 'Bayleef', 'Beautifly', 'Beedrill', 'Beldum', 'Bellossom',
        'Bellsprout', 'Blastoise', 'Blaziken', 'Blissey', 'Breloom', 'Bulbasaur', 'Butterfree',
        'Cacnea', 'Cacturne', 'Camerupt', 'Carvanha', 'Cascoon', 'Castform', 'Caterpie', 'Celebi', 'Chansey',
        'Charizard', 'Charmander', 'Charmeleon', 'Chikorita', 'Chimecho', 'Chinchou', 'Clamperl',
        'Claydol', 'Clefable', 'Clefairy', 'Cleffa', 'Cloyster', 'Combusken', 'Corphish', 'Corsola', 'Cradily',
        'Crawdaunt', 'Crobat', 'Croconaw', 'Cubone', 'Cyndaquil',
        'Delcatty', 'Delibird', 'Deoxys', 'Dewgong', 'Diglett', 'Ditto', 'Dodrio', 'Doduo', 'Donaphan', 'Dragonair',
        'Dragonite', 'Dratini', 'Drowzee', 'Dugtrio', 'Dunsparce', 'Dusclops', 'Duskull', 'Dustox',
        'Eevee', 'Ekans', 'Electabuzz', 'Electrike', 'Electrode', 'Elekid', 'Entei', 'Espeon', 'Exeggcute', 'Exeggutor',
        'Exploud', 'Farfetch', 'Fearow', 'Feebas', 'Feraligatr', 'Flaaffy', 'Flareon', 'Flygon', 'Foretress', 'Furret',
        'Gardevoir', 'Gastly', 'Gengar', 'Geodude', 'Girafarig', 'Glalie', 'Gligar', 'Gloom', 'Golbat', 'Goldeen',
        'Golduck', 'Golem', 'Gorebyss', 'Granbull', 'Graveler', 'Grimer', 'Groundon', 'Grovyle', 'Growlithe', 'Grumpig',
        'Gulpin', 'Gyarados',
        'Hariyama', 'Haunter', 'Heracross', 'Hitmonchan', 'Hitmonlee', 'Hitmontop', 'HoOh', 'HootHoot', 'Hoppip',
        'Horsea', 'Houndoom', 'Houndour', 'Huntail', 'Hypno',
        'Igglybuff', 'Illumise', 'Ivysaur', 'Jigglypuff', 'Jirachi', 'Jolteon', 'Jumpluff', 'Jynx',
        'Kabuto', 'Kabutops', 'Kadabra', 'Kakuna', 'Kangaskhan', 'Kecleon', 'Kingdra', 'Kingler', 'Kirlia', 'Koffing',
        'Krabby', 'Kyogre',
        'Lairon', 'Lanturn', 'Lapras', 'Larvitar', 'Latias', 'Latios', 'Ledian', 'Ledyba', 'Lickitung', 'Lileep',
        'Linoone', 'Lombre', 'Lotad', 'Loudred', 'Ludicolo', 'Lugia', 'Lunatone', 'Luvdisc',
        'Machamp', 'Machoke', 'Machop', 'Magby', 'Magcargo', 'Magikarp', 'Magmar', 'Magnemite', 'Magneton', 'Makuhita',
        'Manectric', 'Mankey', 'Mantine', 'Mareep', 'Marill', 'Marowak', 'Marshtomp', 'Masquerain', 'Mawile',
        'Medicham', 'Meditite', 'Meganium', 'Meowth', 'Metagross', 'Metang', 'Metapod', 'Mew', 'Mewtwo', 'Mightyena',
        'Milotic', 'Miltank', 'Minun', 'Misdreavus',
        'Moltres', 'MrMime', 'Mudkip', 'Muk', 'Murkrow', 'Natu', 'Nidoking', 'Nidoqueen', 'NidoranFemale',
        'NidoranMale', 'Nidorina', 'Nidorino', 'Nincada', 'Ninetales', 'Ninjask', 'Noctowl', 'Nosepass', 'Numel',
        'Nuzleaf', 'Octillery', 'Oddish', 'Omanyte', 'Omastar', 'Onix',
        'Paras', 'Parasect', 'Pelipper', 'Persian', 'Phanpy', 'Pichu', 'Pidgeot', 'Pidgeotto', 'Pidgey', 'Pikachu',
        'Piloswine', 'Pineco', 'Pinsir', 'Plusle', 'Politoed', 'Poliwag', 'Poliwhirl', 'Poliwrath', 'Ponyta',
        'Poochyena', 'Porygon', 'Porygon', 'Primeape', 'Psyduck', 'Pupitar', 'Quagsire', 'Quilava', 'Quilfish',
        'Raichu', 'Raikou', 'Ralts', 'Rapidash', 'Raticate', 'Rattata', 'Rayquaza', 'Reg', 'Regitock', 'Regirock',
        'Relicanth', 'Remoraid', 'Rhydon', 'Rhyhorn', 'Roselia',
        'Salamence', 'Sandshrew', 'Sandslash', 'Sapleye', 'Sceptile', 'Schuckle', 'Scizor', 'Scyther', 'Seadra',
        'Seaking', 'Sealeo', 'Seedot', 'Seel', 'Sellow', 'Sentret', 'Seviper', 'Sharpedo', 'Shedinja', 'Shelgon',
        'Shellder', 'Shiftry', 'Shroomish', 'Shuppet', 'Silcoon', 'Skarmony', 'Skiploom', 'Skitty', 'Slaking',
        'Slakoth', 'Slowbro', 'Slowking', 'Slowpoke', 'Slugma', 'Smeargle', 'Smoochum', 'Sneazle', 'Snorlax', 'Snorunt',
        'Snubbull', 'Sol', 'Spearow', 'Spheal', 'Spinarak', 'Spinda', 'Spoink', 'Squirtle', 'Stantler', 'Starmie',
        'Staryu', 'Steelix', 'Sudowoodo', 'Suicune', 'Sunflora', 'Sunkern', 'Surskit', 'Swablu', 'Swalot', 'Swampert',
        'Swinub',
        'Taillow', 'Tangela', 'Tauros', 'Teddiursa', 'Tentacool', 'Tentacruel', 'Togepi', 'Togetic', 'Torchic',
        'Torkoal', 'Totodile', 'Trapinch', 'Treecko', 'Tropius', 'Typhlosion', 'Tyranitar', 'Tyrogue',
        'Umbreon', 'Unown', 'Ursaring', 'Vaporeon', 'Venomoth', 'Venonat', 'Venusaur', 'Vibrava', 'Victreebel',
        'Vigoroth', 'Vileplume', 'Volbeat', 'Voltorb', 'Vulpix',
        'Wailmer', 'Wailord', 'Walrein', 'Wartortle', 'Weedle', 'Weepinbell', 'Weezing', 'Whiscash', 'Whismur',
        'Wigglytuff', 'Wingull', 'Woobuffet', 'Wooper', 'Wurmple', 'Wynaut', 'Xatu', 'Yanma', 'Zangoose', 'Zapdos',
        'Zigzagoon', 'Zubat']
    return data


def get_data_shuffled():
    data = get_data()
    from random import shuffle

    shuffled = data
    shuffle(shuffled)
    return shuffled


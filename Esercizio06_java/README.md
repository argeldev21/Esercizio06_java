Codice SQL per creare le tabelle e impostare le chiavi primarie ed esterne:

-- TABELLA OSPITI
CREATE TABLE ospiti (
    id_ospite INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    cognome VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    telefono VARCHAR(20)
);

-- TABELLA CAMERE
CREATE TABLE camere (
    id_camera INT PRIMARY KEY AUTO_INCREMENT,
    numero_camera INT NOT NULL UNIQUE,
    tipologia ENUM('Singola', 'Doppia', 'Suite') NOT NULL
);

-- TABELLA PRENOTAZIONI
CREATE TABLE prenotazioni (
    id_prenotazione INT PRIMARY KEY AUTO_INCREMENT,
    ospite_id INT NOT NULL,
    camera_id INT NOT NULL,
    check_in DATE NOT NULL,
    check_out DATE NOT NULL,
    numero_persone INT NOT NULL CHECK (numero_persone > 0),
    FOREIGN KEY (ospite_id) REFERENCES ospiti(id_ospite),
    FOREIGN KEY (camera_id) REFERENCES camere(id_camera)
);

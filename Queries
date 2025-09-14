CREATE DATABASE SportManagement;
USE SportManagement;

CREATE TABLE Sport (
    sport_id INT AUTO_INCREMENT PRIMARY KEY,
    sport_name VARCHAR(50) NOT NULL,
    category VARCHAR(20)
);

CREATE TABLE Player (
    player_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    gender VARCHAR(10),
    sport_id INT,
    FOREIGN KEY (sport_id) REFERENCES Sport(sport_id)
);

CREATE TABLE Coach (
    coach_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    experience_years INT,
    sport_id INT,
    FOREIGN KEY (sport_id) REFERENCES Sport(sport_id)
);

CREATE TABLE Team (
    team_id INT AUTO_INCREMENT PRIMARY KEY,
    team_name VARCHAR(100),
    coach_id INT,
    FOREIGN KEY (coach_id) REFERENCES Coach(coach_id)
);

CREATE TABLE Player_Team (
    player_id INT,
    team_id INT,
    PRIMARY KEY (player_id, team_id),
    FOREIGN KEY (player_id) REFERENCES Player(player_id),
    FOREIGN KEY (team_id) REFERENCES Team(team_id)
);

CREATE TABLE Matches (
    match_id INT AUTO_INCREMENT PRIMARY KEY,
    team1_id INT,
    team2_id INT,
    date DATE,
    location VARCHAR(100),
    winner_team_id INT,
    FOREIGN KEY (team1_id) REFERENCES Team(team_id),
    FOREIGN KEY (team2_id) REFERENCES Team(team_id),
    FOREIGN KEY (winner_team_id) REFERENCES Team(team_id)
);

INSERT INTO Sport (sport_name, category) VALUES
('Football', 'Outdoor'),
('Basketball', 'Indoor'),
('Cricket', 'Outdoor'),
('Tennis', 'Outdoor'),
('Volleyball', 'Indoor'),
('Badminton', 'Indoor'),
('Hockey', 'Outdoor'),
('Table Tennis', 'Indoor'),
('Rugby', 'Outdoor'),
('Handball', 'Indoor');

INSERT INTO Coach (name, experience_years, sport_id) VALUES
('John Doe', 10, 1),
('Emily Smith', 8, 2),
('Raj Patel', 12, 3),
('Sophia Green', 5, 4),
('Liam Brown', 7, 5),
('Emma Johnson', 9, 6),
('William Lee', 6, 7),
('Olivia Davis', 11, 8),
('Noah Wilson', 3, 9),
('Ava Martinez', 4, 10);

INSERT INTO Team (team_name, coach_id) VALUES
('Tigers', 1),
('Eagles', 2),
('Warriors', 3),
('Panthers', 4),
('Sharks', 5),
('Dragons', 6),
('Falcons', 7),
('Lions', 8),
('Bulls', 9),
('Wolves', 10);

INSERT INTO Player (name, age, gender, sport_id) VALUES
('Alice', 22, 'Female', 2),
('Bob', 24, 'Male', 1),
('Charlie', 21, 'Male', 1),
('Diana', 23, 'Female', 2),
('Ethan', 25, 'Male', 3),
('Fiona', 20, 'Female', 4),
('George', 26, 'Male', 5),
('Hannah', 22, 'Female', 6),
('Ian', 27, 'Male', 7),
('Julia', 21, 'Female', 8),
('Kevin', 23, 'Male', 9),
('Laura', 24, 'Female', 10),
('Mike', 22, 'Male', 1),
('Nina', 23, 'Female', 2),
('Oscar', 20, 'Male', 3);

INSERT INTO Player_Team VALUES
(1, 2), (2, 1), (3, 1), (4, 2),
(5, 3), (6, 4), (7, 5), (8, 6),
(9, 7), (10, 8), (11, 9), (12, 10),
(13, 1), (14, 2), (15, 3);

INSERT INTO Matches (team1_id, team2_id, date, location, winner_team_id) VALUES
(1, 2, '2025-05-10', 'Stadium A', 1),
(2, 1, '2025-05-17', 'Stadium B', 2),
(3, 4, '2025-06-01', 'Stadium C', 3),
(5, 6, '2025-06-05', 'Stadium D', 6),
(7, 8, '2025-06-10', 'Stadium E', 7),
(9, 10, '2025-06-12', 'Stadium F', 9),
(1, 3, '2025-06-15', 'Stadium A', 1),
(4, 2, '2025-06-18', 'Stadium B', 4),
(5, 7, '2025-06-21', 'Stadium C', 5),
(6, 8, '2025-06-25', 'Stadium D', 8);

SELECT * FROM Player;

-- 1. List all players
SELECT * FROM Player;

-- 2. List all teams with their coach name
SELECT T.team_name, C.name AS coach_name
FROM Team T JOIN Coach C ON T.coach_id = C.coach_id;

-- 3. List all matches with team names and winner
SELECT M.date, T1.team_name AS Team1, T2.team_name AS Team2, TW.team_name AS Winner
FROM Matches M
JOIN Team T1 ON M.team1_id = T1.team_id
JOIN Team T2 ON M.team2_id = T2.team_id
JOIN Team TW ON M.winner_team_id = TW.team_id;

-- 4. Show all players in team 'Tigers'
SELECT P.name
FROM Player P
JOIN Player_Team PT ON P.player_id = PT.player_id
JOIN Team T ON PT.team_id = T.team_id
WHERE T.team_name = 'Tigers';

-- 5. List all players of a particular sport (e.g., Football)
SELECT P.name, S.sport_name
FROM Player P
JOIN Sport S ON P.sport_id = S.sport_id
WHERE S.sport_name = 'Football';

-- 6. Show total matches played by each team
SELECT T.team_name, COUNT(*) AS matches_played
FROM Team T
JOIN Matches M ON T.team_id = M.team1_id OR T.team_id = M.team2_id
GROUP BY T.team_name;

-- 7. Show win count for each team
SELECT T.team_name, COUNT(*) AS wins
FROM Team T
JOIN Matches M ON T.team_id = M.winner_team_id
GROUP BY T.team_name;

-- 8. Find coaches with more than 5 years experience
SELECT name FROM Coach WHERE experience_years > 5;

-- 9. Find all indoor sports
SELECT sport_name FROM Sport WHERE category = 'Indoor';

-- 10. List all teams coached by 'Emily Smith'
SELECT team_name FROM Team
JOIN Coach ON Team.coach_id = Coach.coach_id
WHERE Coach.name = 'Emily Smith';





# telediabetology
-- Create table for villages
CREATE TABLE Villages (
    VillageID INT PRIMARY KEY,
    VillageName VARCHAR(100),
    District VARCHAR(100),
    State VARCHAR(100)
);

-- Create table for individuals
CREATE TABLE Individuals (
    IndividualID INT PRIMARY KEY,
    VillageID INT,
    Age INT,
    Gender VARCHAR(10),
    DiabetesStatus VARCHAR(10), -- "Diabetic" or "Non-diabetic"
    FOREIGN KEY (VillageID) REFERENCES Villages(VillageID)
);

-- Create table for diabetes screening results
CREATE TABLE ScreeningResults (
    ScreeningID INT PRIMARY KEY,
    IndividualID INT,
    ScreeningDate DATE,
    FastingGlucose DECIMAL(5,2),
    DiabetesConfirmed VARCHAR(5), -- "Yes" or "No"
    ComplicationsDetected VARCHAR(100), -- Comma-separated list of complications
    FOREIGN KEY (IndividualID) REFERENCES Individuals(IndividualID)
);

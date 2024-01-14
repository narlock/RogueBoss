# Rogue Boss
Simple "Boss Battle" simulator for building communities.

![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-F2F4F9?style=for-the-badge&logo=spring-boot)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white)

## Application Description

Rogue Boss is an application that implements mini "boss battles" for users to interact with a front end. A boss is chosen randomly from a list, given a type (see types). Users can attack the boss via an open-front end implementation provided by developers that utilize Rogue Boss. Rogue Boss acts as a back end application that can receive RESTful API requests to attack the boss while also storing boss data locally using a JSON format. Rogue Boss also implements a simple GUI that contains a simple animation and health bar indicating the current status of each events that are send via the API.

This application as it stands leaves choices for other developers on how they want to call the API. This application is not responsible for providing a front end interface for calling the API.

## GUI Screenshots
![RB1](./README%20Assets/RB1.png)
![RB2](./README%20Assets/RB2.png)


## API Specification

### GET `/rb`
Pings the Rogue Boss application. This should be utilized to ensure connection to the API is stable and that the GUI displays the correct boss information.

**Response**
```
HTTP/1.1 200 OK
Content-Type: text/plain

Success
```
### POST `/rb`
Send an attack request. Request body should contain unique information with respect to the calling user.

**Request**
```json
POST /rb

{
    "id": "123",
    "name": "Trinity",
    "type": "DARK",
    "model": "TRINITY",
    "weapon": 1,
    "powerUp": 1,
    "exp": 2000
}
```

**Response**
```json
HTTP/1.1 200 OK
Content-Type: application/json

{
    "note": "Critical hit! 6 damage dealt.",
    "slain": false,
    "boss": {
        "level": 3,
        "bossType": "SLIME",
        "type": "DARK",
        "health": 1290,
        "damageList": [
            {
                "id": "123",
                "damage": 6
            }
        ],
        "name": "DARK SLIME LV3"
    }
}
```

The `damageList` attribute of the response will contain information of each user attacking the boss. The `damage` sub-attribute will add the new damage number indicated by the `note` field.

## Typing
This game has a simple typing system. Certain types are super/not very effective against one another.

- 🔥 **FIRE** is weak to **WATER**, but super effective against **EARTH**.
- 💧 **WATER** is weak to **EARTH**, but super effective against **FIRE**.
- 🪨 **EARTH** is weak to **FIRE**, but super effective against **WATER**.
- 🔮 **PSYCHIC** is weak to **LIGHT**, but super effective against **DARK**.
- 💫 **LIGHT** is weak to **DARK**, but super effective against **PSYCHIC**.
- 🌑 **DARK** is weak to **PSYCHIC**, but super effective against **LIGHT**.


## Future Improvements
- Unit Testing
- Simple Architectural Diagram
- Add additional images
- Potentially utilize `weapon` and `powerUp` attributes.

## Artwork Usage
The artwork in narlock's RogueBoss were created by __narlock__. Please ask for permission if you plan to use these assets for your own projects.

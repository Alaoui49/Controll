# 📦 Gestion de Campagnes de Dons - Spring Boot REST API

Mini projet réalisé dans le cadre du module **Architecture JEE** – IIR G6  
Encadré par **Pr. Ahaidous Khadija**  
Durée : 2h

## 🎯 Objectif

Développer une API REST avec Spring Boot permettant la **gestion de campagnes de dons** ainsi que le **suivi des contributions des donateurs**.  
Ce projet utilise une base de données **H2 en mémoire**, avec un modèle orienté **JPA** et des endpoints exposés via **Spring Web**.

---

## 🛠️ Technologies utilisées

- Java 17
- Spring Boot
- Spring Web
- Spring Data JPA
- H2 Database (en mémoire)
- Jakarta Validation
- Springdoc OpenAPI (Swagger)
- Maven
- IntelliJ IDEA

---

## 📐 Modèle de données

### 📁 Entités principales

#### `Donateur`
| Champ           | Type         |
|----------------|--------------|
| id             | Long         |
| nom            | String       |
| objectifMontant| Double       |
| dateDebut      | LocalDate    |
| dateFin        | LocalDate    |

#### `SuiviDonateur`
| Champ         | Type         |
|---------------|--------------|
| id            | Long         |
| campagne      | Donateur (ManyToOne) |
| nomDonateur   | String       |
| montant       | Double       |
| date          | LocalDate    |

---

## 📦 Fonctionnalités

- ✅ CRUD complet sur les **donateurs**
- ✅ Récupération des **donateurs actifs** (dateFin > aujourd’hui)
- ✅ Validation des champs via `@Valid` (ex : nom obligatoire, date non nulle, etc.)
- ✅ Base de données en mémoire (H2) avec console web activée
- ✅ Documentation interactive avec Swagger (bonus)

---

## 🔁 Endpoints principaux

| Méthode | URL                              | Description                            |
|--------|----------------------------------|----------------------------------------|
| `GET`  | `/api/donateurs`                 | Lister tous les donateurs              |
| `GET`  | `/api/donateurs/actifs`          | Lister les donateurs actifs            |
| `POST` | `/api/donateurs`                 | Ajouter un nouveau donateur            |
| `DELETE`| `/api/donateurs/{id}`           | Supprimer un donateur par ID           |

---

## 🧪 Test de l’API

Lancement :         
Accès :
- Swagger UI : [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)
- H2 Console : [http://localhost:8080/h2-console](http://localhost:8080/h2-console)  
  (JDBC URL: `jdbc:h2:mem:testdb`, username: `sa`, pas de mot de passe)

---

## 🧾 Exemples JSON

### Donateur (POST `/api/donateurs`)
```json
{
  "nom": "Campagne Ramadan",
  "objectifMontant": 10000,
  "dateDebut": "2025-04-01",
  "dateFin": "2025-05-01"
}


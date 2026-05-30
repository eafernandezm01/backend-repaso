# Backend para repasar y conectarte desde angular

## TIPS
# Paso 1. Analizar la respuesta JSON
Antes de programar nada, accede al endpoint desde el navegador o mediante Postman y analiza cuidadosamente la estructura de la respuesta.

Preguntas que debes hacerte:
- ¿Devuelve un objeto o un array?
- ¿Existen objetos dentro de otros objetos?
- ¿Existen arrays dentro de objetos?
- ¿Existen arrays de objetos?
- ¿Qué tipos de datos tiene cada propiedad?

# Paso 2. Crear el modelo TypeScript
Una vez analizado el JSON, crea la interfaz o interfaces necesarias. 
Acorde a los datos devueltos (ten en cuenta el tipo) y escribe igual el nombre de cada atributo para que se mapee automáticamente.
Si aparecen objetos anidados, crea interfaces independientes para cada uno.


# Paso 3. Crear el servicio Angular
Genera un servicio utilizando Angular CLI:
```bash
ng g s services/nombre-servicio
Importa en el constructor:

```typescript
HttpClient
```
No olvides de poner el provider provideHttpClient() en el app.config.ts 
Genera un método para poder llamar al servicio, no olvides que devuelve un observable.

# Paso 4. Crear el componente
Genera un componente página para mostrar la información.

Ejemplo:

```bash
ng g c pages/nombre-pagina
```

# Paso 5. Consumir el servicio
Inyecta el servicio en el componente.
Ejemplo:
```typescript
constructor(private apiService: ApiService) {}
```
Realiza la petición:
---

```typescript
ngOnInit() {
    this.apiService.getNombreServicio()
        .subscribe(data => {
            this.atributo = data;
        });
}
```
Siendo atributo un atributo del componente, debe ser del mismo tipo devuelto.

# Paso 6. Mostrar la información
- Si es un array debes recorrer para mostrar la información  @for
        Podrás pasárlo a un componente hijo o pintarlo en la propia página

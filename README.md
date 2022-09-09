# Introducción JavaScript - TypeScript

## Ejercicios JavaScript

### Ejercicio 1

Crea un parseador que reciba un string en formato CSV y devuelva una colección de objetos. Utiliza destructuring, rest y spread operator donde creas conveniente.

- Código

```
const data = `id,name,surname,gender,email,picture
15519533,Raul,Flores,male,raul.flores@example.com,https://randomuser.me/api/portraits/men/42.jpg
82739790,Alvaro,Alvarez,male,alvaro.alvarez@example.com,https://randomuser.me/api/portraits/men/48.jpg
37206344,Adrian,Pastor,male,adrian.pastor@example.com,https://randomuser.me/api/portraits/men/86.jpg
58054375,Fatima,Guerrero,female,fatima.guerrero@example.com,https://randomuser.me/api/portraits/women/74.jpg
35133706,Raul,Ruiz,male,raul.ruiz@example.com,https://randomuser.me/api/portraits/men/78.jpg
79300902,Nerea,Santos,female,nerea.santos@example.com,https://randomuser.me/api/portraits/women/61.jpg
89802965,Andres,Sanchez,male,andres.sanchez@example.com,https://randomuser.me/api/portraits/men/34.jpg
62431141,Lorenzo,Gomez,male,lorenzo.gomez@example.com,https://randomuser.me/api/portraits/men/81.jpg
05298880,Marco,Campos,male,marco.campos@example.com,https://randomuser.me/api/portraits/men/67.jpg
61539018,Marco,Calvo,male,marco.calvo@example.com,https://randomuser.me/api/portraits/men/86.jpg`;

const fromCSV = (csv) => {
    const linesArray = csv.split('\n');
    const keysArray = linesArray[0].split(',');
    return linesArray.slice(1).map(lineArray => {
        return lineArray.split(',').reduce((lines, line, i) => {
            const objPerson = {};
            objPerson[keysArray[i]] = line;
            return { ...lines, ...objPerson };
        }, {});
    });
};

const result = fromCSV(data);
console.log(result);
```
- Resultado 

```
[
  {
    id: '15519533',
    name: 'Raul',
    surname: 'Flores',
    gender: 'male',
    email: 'raul.flores@example.com',
    picture: 'https://randomuser.me/api/portraits/men/42.jpg'
  },
  {
    id: '82739790',
    name: 'Alvaro',
    surname: 'Alvarez',
    gender: 'male',
    email: 'alvaro.alvarez@example.com',
    picture: 'https://randomuser.me/api/portraits/men/48.jpg'
  },
  {
    id: '37206344',
    name: 'Adrian',
    surname: 'Pastor',
    gender: 'male',
    email: 'adrian.pastor@example.com',
    picture: 'https://randomuser.me/api/portraits/men/86.jpg'
  },
  {
    id: '58054375',
    name: 'Fatima',
    surname: 'Guerrero',
    gender: 'female',
    email: 'fatima.guerrero@example.com',
    picture: 'https://randomuser.me/api/portraits/women/74.jpg'
  },
  {
    id: '35133706',
    name: 'Raul',
    surname: 'Ruiz',
    gender: 'male',
    email: 'raul.ruiz@example.com',
    picture: 'https://randomuser.me/api/portraits/men/78.jpg'
  },
  {
    id: '79300902',
    name: 'Nerea',
    surname: 'Santos',
    gender: 'female',
    email: 'nerea.santos@example.com',
    picture: 'https://randomuser.me/api/portraits/women/61.jpg'
  },
  {
    id: '89802965',
    name: 'Andres',
    surname: 'Sanchez',
    gender: 'male',
    email: 'andres.sanchez@example.com',
    picture: 'https://randomuser.me/api/portraits/men/34.jpg'
  },
  {
    id: '62431141',
    name: 'Lorenzo',
    surname: 'Gomez',
    gender: 'male',
    email: 'lorenzo.gomez@example.com',
    picture: 'https://randomuser.me/api/portraits/men/81.jpg'
  },
  {
    id: '05298880',
    name: 'Marco',
    surname: 'Campos',
    gender: 'male',
    email: 'marco.campos@example.com',
    picture: 'https://randomuser.me/api/portraits/men/67.jpg'
  },
  {
    id: '61539018',
    name: 'Marco',
    surname: 'Calvo',
    gender: 'male',
    email: 'marco.calvo@example.com',
    picture: 'https://randomuser.me/api/portraits/men/86.jpg'
  }
]
```

Extra: Añade un segundo argumento a la función para indicar el número de atributos a añadir. Si dicho argumento no es informado cada objeto tendrá todos los atributos.

```
const fromCSV = (csv, nAttrs) => {};

console.log(fromCSV(data)); // Cada usuario tendrá todos los atributos como la implementación original
console.log(fromCSV(data, 2)); // cada usuario tendrá sólo `id` y `name`
console.log(fromCSV(data, 3)); // cada usuario tendrá sólo `id`, `name` y `surname`
console.log(fromCSV(data, 4)); // cada usuario tendrá sólo `id`, `name`, `surname` y `gender`
```

### Ejercicio 2

Implementar una funcion ```replaceAt``` que tome como primer argumento un array, como segundo argumento un índice y como tercer argumento un valor y reemplace el elemento dentro del array en el índice indicado. El array de entrada no debe de ser mutado, eso es, que debes crear un nuevo array sin modificar el existente. Utiliza spread operator, y ```slice``` para conseguirlo.

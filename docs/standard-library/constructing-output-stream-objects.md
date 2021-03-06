---
title: Construir objetos de flujo de salida
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: d7bec211f30986deccc869a879dd5155ea70996b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457280"
---
# <a name="constructing-output-stream-objects"></a>Construir objetos de flujo de salida

Si solo usa los objeto predefinidos `cout`, `cerr` o `clog`, no es necesario que cree un flujo de salida. Debe usar constructores para:

- [Constructores de flujo de archivos de salida](#vclrfoutputfilestreamconstructorsanchor1)

- [Constructores de flujo de cadenas de salida](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a> Constructores de flujo de archivos de salida

Puede crear un flujo de archivo de salida de una de estas dos maneras:

- Use el constructor predeterminado y después llame a la función miembro `open`.

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- Especifique un nombre de archivo y marcas de modo en la llamada al constructor.

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a> Constructores de flujo de cadenas de salida

Para crear un flujo de cadenas de salida, puede usar `ostringstream` de la siguiente manera:

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

El "manipulador" `ends` agrega el carácter nulo de terminación necesario a la cadena.

## <a name="see-also"></a>Vea también

[Flujos de salida](../standard-library/output-streams.md)

---
title: Flujos de entrada / salida
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: d426baacb52095ab2d933263fdac8e312fc29558
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159241"
---
# <a name="inputoutput-streams"></a>Flujos de entrada/salida

`basic_iostream`, que se define en el archivo de encabezado \<istream>, es la plantilla de clase para los objetos que administran flujos de E/S basados en caracteres de entrada y de salida.

Hay dos definiciones de tipo que definen las especializaciones específicas de caracteres de `basic_iostream` y que pueden facilitar la lectura del código: `iostream` (que no se debe confundirse con el archivo de encabezado \<iostream>) es un flujo de E/S basado en `basic_iostream<char>` y `wiostream` es un flujo de E/S basado en `basic_iostream<wchar_t>`.

Para obtener más información, vea [Clase basic_iostream](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md) y [wiostream](../standard-library/basic-iostream-class.md).

De `basic_iostream` deriva la plantilla de clase `basic_fstream`, que se usa para transmitir datos de caracteres a y desde archivos.

También hay definiciones de tipos que proporcionan especializaciones específicas de caracteres de `basic_fstream`. Son `fstream`, que es una secuencia de E/S de archivo que se basa en **char**, y `wfstream`, que es una secuencia de E/S de archivo que se basa en **wchar_t**. Para obtener más información, vea [Clase basic_fstream](../standard-library/basic-fstream-class.md), [fstream](../standard-library/basic-fstream-class.md) y [wfstream](../standard-library/basic-fstream-class.md). El uso de estas definiciones de tipos requiere la inclusión del archivo de encabezado \<fstream>.

> [!NOTE]
> Cuando se usa un objeto `basic_fstream` para realizar operaciones de E/S de archivos, aunque el búfer subyacente contenga posiciones designadas de forma independiente para la lectura y la escritura, las posiciones de la entrada actual y de la salida actual están vinculadas y, por lo tanto, la lectura de algunos datos mueve la posición de salida.

La plantilla de clase `basic_stringstream` y su especialización común, `stringstream`, se usan a menudo para trabajar con objetos de flujo de E/S para insertar y extraer datos de caracteres. Para obtener más información, vea [Clase basic_stringstream](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Vea también

[stringstream](../standard-library/basic-stringstream-class.md)<br/>
[basic_stringstream (Clase)](../standard-library/basic-stringstream-class.md)<br/>
[\<sstream>](../standard-library/sstream.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>

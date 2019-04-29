---
title: Palabras reservadas
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 7d51f599dfb81dfa860e1bdba86c4372e80379fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319426"
---
# <a name="reserved-words"></a>Palabras reservadas

Las siguientes palabras están reservadas por el vinculador. Estos nombres se pueden utilizar como argumentos en [instrucciones de definición de módulo](module-definition-dot-def-files.md) solo si el nombre está entre comillas dobles ("").

||||
|-|-|-|
|**OBJETO APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**CARGA PREVIA**|
|**BASE**|**IOPL**|**PRIVATE**|
|**CODE**|**LIBRARY**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**CONFORME**|**LOADONCALL**<sup>1</sup>|**PURO**<sup>1</sup>|
|**DATOS**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**DESCRIPCIÓN**|**MOVABLE**<sup>1</sup>|**LECTURA Y ESCRITURA**|
|**DEV386**|**MOVEABLE**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**DISCARDABLE**|**VARIOS**|**RESIDENTE**|
|**DYNAMIC**|**NAME**|**RESIDENTNAME**<sup>1</sup>|
|**EXECUTE-ONLY**|**NEWFILES**<sup>2</sup>|**SECCIONES**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTS**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**COMPARTIDO**|
|**EXETYPE**|**NONAME**|**ÚNICO**|
|**EXPORTS**|**NO CONFORMES**<sup>1</sup>|**STACKSIZE**|
|**FIJO**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**FUNCIONES**<sup>2</sup>|**NINGUNO**|**VERSION**|
|**HEAPSIZE**|**NO COMPARTIDOS**|**WINDOWAPI**|
|**IMPORTS**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMPURAS**<sup>1</sup>|**OBJETOS**|**WINDOWS**|
|**INCLUIR**<sup>2</sup>|**ANTIGUO**<sup>1</sup>||

<sup>1</sup> el enlazador emite una advertencia ("omitida") cuando encuentra este término. Sin embargo, se sigue reserva la palabra.

<sup>2</sup> el vinculador omite esta palabra, pero no genera ninguna advertencia.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
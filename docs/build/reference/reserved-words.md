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
ms.openlocfilehash: 360baf479f9100483fe694ca8860dfc1d7ebfe11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502471"
---
# <a name="reserved-words"></a>Palabras reservadas

Las siguientes palabras están reservadas por el vinculador. Estos nombres se pueden utilizar como argumentos en [instrucciones de definición de módulo](../../build/reference/module-definition-dot-def-files.md) solo si el nombre está entre comillas dobles ("").

||||
|-|-|-|
|**OBJETO APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**CARGA PREVIA**|
|**BASE**|**IOPL**|**PRIVADO**|
|**CÓDIGO**|**BIBLIOTECA**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**CONFORME**|**LOADONCALL**<sup>1</sup>|**PURO**<sup>1</sup>|
|**DATOS**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**DESCRIPCIÓN**|**PUEDE MOVER**<sup>1</sup>|**LECTURA Y ESCRITURA**|
|**DEV386**|**MOVEABLE**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**PUEDE DESCARTAR**|**VARIOS**|**RESIDENTE**|
|**DINÁMICO**|**NOMBRE**|**RESIDENTNAME**<sup>1</sup>|
|**SOLO PARA EJECUTAR**|**NEWFILES**<sup>2</sup>|**SECCIONES**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTOS**|
|**EJECUCIÓNLECTURA**|**NOIOPL**<sup>1</sup>|**COMPARTIDO**|
|**EXETYPE**|**NONAME**|**ÚNICO**|
|**EXPORTS**|**NO CONFORMES**<sup>1</sup>|**STACKSIZE**|
|**FIJO**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**FUNCIONES**<sup>2</sup>|**NINGUNO**|**VERSIÓN**|
|**HEAPSIZE**|**NO COMPARTIDOS**|**WINDOWAPI**|
|**IMPORTACIONES**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMPURAS**<sup>1</sup>|**OBJETOS**|**WINDOWS**|
|**INCLUIR**<sup>2</sup>|**ANTIGUO**<sup>1</sup>||

<sup>1</sup> el enlazador emite una advertencia ("omitida") cuando encuentra este término. Sin embargo, se sigue reserva la palabra.

<sup>2</sup> el vinculador omite esta palabra, pero no genera ninguna advertencia.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
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
ms.openlocfilehash: 16caacb77e052eebc8e2cd101990ee373535bd6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171156"
---
# <a name="reserved-words"></a>Palabras reservadas

El enlazador reserva las siguientes palabras. Estos nombres se pueden usar como argumentos en las [instrucciones de definición de módulos](module-definition-dot-def-files.md) solo si el nombre está entre comillas dobles ("").

||||
|-|-|-|
|**Apploader**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**CARGAR previamente**|
|**BÁSICA**|**IOPL**|**PRIVADA**|
|**CODIFICA**|**Biblioteca**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**CONFORME**|**LOADONCALL**<sup>1</sup>|**Puro**<sup>1</sup>|
|**DATA**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**DESCRIPCIÓN**|**Movible**<sup>1</sup>|**ESCRITURA**|
|**DEV386**|**Móvil**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**DESCARTABLE**|**DIVERSOS**|**LASERPREP**|
|**DINÁMICA**|**NOMBRE**|**RESIDENTNAME**<sup>1</sup>|
|**SOLO EJECUCIÓN**|**Archivo newfiles**<sup>2</sup>|**SECCIÓN**|
|**EXECUTEONLY**|**NoData**<sup>1</sup>|**SECTORES**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**RECURSO**|
|**EXETYPE**|**NONAME**|**SENCILLA**|
|**EXPORTS**|No **compatible**<sup>1</sup>|**STACKSIZE**|
|**Fijo**<sup>1</sup>|**No descartable**|**STUB**|
|**Funciones**<sup>2</sup>|**NONE**|**VERSION**|
|**HEAPSIZE**|**NO compartidos**|**WINDOWAPI**|
|**IMPORTA**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMpuración**<sup>1</sup>|**LOS**|**WINDOWS**|
|**Incluir**<sup>2</sup>|**Antigua**<sup>1</sup>||

<sup>1</sup> el enlazador emite una advertencia ("omitida") cuando encuentra este término. Sin embargo, la palabra todavía está reservada.

<sup>2</sup> el enlazador omite esta palabra pero no emite ninguna advertencia.

## <a name="see-also"></a>Consulte también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)

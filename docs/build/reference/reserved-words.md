---
title: Palabras reservadas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 132bd8e5ba66cbf9486a6da4747994c667e2f6e7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705665"
---
# <a name="reserved-words"></a>Palabras reservadas

Las siguientes palabras están reservadas por el vinculador. Estos nombres pueden utilizarse como argumentos en [las instrucciones de definición de módulo](../../build/reference/module-definition-dot-def-files.md) solo si el nombre se incluye entre comillas dobles ("").

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**PRECARGA**|
|**BASE**|**IOPL**|**PRIVADA**|
|**CÓDIGO**|**BIBLIOTECA**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**CONFORME**|**LOADONCALL**<sup>1</sup>|**PURO**<sup>1</sup>|
|**DATOS**|**LONGNAMES**<sup>2</sup>|**SOLO LECTURA**|
|**DESCRIPCIÓN**|**PUEDE MOVER**<sup>1</sup>|**LECTURA Y ESCRITURA**|
|**DEV386**|**MOVEABLE**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**DESCARTABLE**|**VARIOS**|**RESIDENTE**|
|**DINÁMICA**|**NOMBRE**|**RESIDENTNAME**<sup>1</sup>|
|**SOLO PARA EJECUTAR**|**NEWFILES**<sup>2</sup>|**SECCIONES**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTOS**|
|**EJECUCIÓNLECTURA**|**NOIOPL**<sup>1</sup>|**COMPARTIDO**|
|**EXETYPE**|**NONAME**|**ÚNICO**|
|**EXPORTS**|**NO CUMPLEN LAS ESPECIFICACIONES**<sup>1</sup>|**STACKSIZE**|
|**FIJO**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**FUNCIONES**<sup>2</sup>|**NINGUNO**|**VERSIÓN**|
|**HEAPSIZE**|**NO COMPARTIDOS**|**WINDOWAPI**|
|**IMPORTACIONES**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMPURAS**<sup>1</sup>|**OBJETOS**|**WINDOWS**|
|**INCLUIR**<sup>2</sup>|**ANTIGUO**<sup>1</sup>||

<sup>1</sup> el vinculador emite una advertencia ("omitida") cuando encuentra este término. Sin embargo, la palabra se sigue reserva.

<sup>2</sup> el vinculador omite esta palabra, pero no genera ninguna advertencia.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
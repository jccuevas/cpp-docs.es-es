---
title: Las herramientas de compilación de C/c ++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- c.build
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a6a223e092e7ad31dd263142d2a87712eaf556b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726042"
---
# <a name="cc-build-tools"></a>Herramientas de compilación de C/C++

Visual C++ proporciona las siguientes herramientas de línea de comandos para ver y manipular el resultado de la compilación:

- [BSCMAKE. EXE](../../build/reference/bscmake-reference.md) genera un archivo de información de examen (.bsc) que contiene información sobre los símbolos (clases, funciones, datos, macros y tipos) en el programa. Ver esta información en ventanas de exploración en el entorno de desarrollo. (Un archivo .bsc también se puede compilar en el entorno de desarrollo.)

- [LIB. EXE](../../build/reference/lib-reference.md) se usa para crear y administrar una biblioteca de archivos de objeto de formato de archivo de objeto común (COFF). También puede utilizarse para crear archivos de exportación e importe las bibliotecas a las definiciones de referencia que se exportan.

- [EDITBIN. EXE](../../build/reference/editbin-reference.md) se usa para modificar los archivos binarios de COFF.

- [DUMPBIN. EXE](../../build/reference/dumpbin-reference.md) muestra información (por ejemplo, una tabla de símbolos) acerca de los archivos binarios de COFF.

- [NMAKE](../../build/nmake-reference.md) lee y ejecuta archivos MAKE.

- [ERRLOOK](../../build/reference/value-edit-control.md), la utilidad de búsqueda de errores, se recupera un mensaje de error del sistema o un mensaje de error de módulo según el valor especificado.

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Nombres representativos](../../build/reference/decorated-names.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
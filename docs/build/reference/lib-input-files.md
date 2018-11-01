---
title: Archivos de entrada de LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 885d03e74c7acff54e527c2dbad38de055913b5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503337"
---
# <a name="lib-input-files"></a>Archivos de entrada de LIB

Los archivos de entrada que espera LIB dependen del modo en el que se esté utilizando, tal como se muestra en la tabla siguiente.

|Modo|Entrada|
|----------|-----------|
|Predeterminado (generar o modificar una biblioteca)|Archivos de objeto (.obj) COFF, bibliotecas COFF (.lib), archivos de objeto (.obj) del formato de modelo de objeto (OMF) de 32 bits|
|Extraer a un miembro con/Extract|Biblioteca COFF (.lib)|
|Creación de una exportación de archivo e importar biblioteca con la opción /DEF|Archivo de definición de módulo (.def), archivos objeto (.obj) COFF, bibliotecas COFF (.lib), archivos de objeto (.obj) OMF de 32 bits|

> [!NOTE]
>  No se puede usar bibliotecas OMF creadas con la versión de 16 bits de LIB como entrada para la versión de 32 bits de LIB.

## <a name="see-also"></a>Vea también

[Información general sobre LIB](../../build/reference/overview-of-lib.md)
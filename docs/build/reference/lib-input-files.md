---
title: Archivos de entrada de LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: fb0095bd9e8699fbc9a1a144833d12d2cf4a1f83
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423097"
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

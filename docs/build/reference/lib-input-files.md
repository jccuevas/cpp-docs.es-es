---
title: Archivos de entrada de LIB
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 209ba04ea43116b39f28b0790b7a1e2b3fb5ccd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439455"
---
# <a name="lib-input-files"></a>Archivos de entrada de LIB

Los archivos de entrada esperados por LIB dependen del modo en el que se utiliza, como se muestra en la tabla siguiente.

|Mode|Entrada|
|----------|-----------|
|Predeterminado (generar o modificar una biblioteca)|Archivos de objeto COFF (. obj), bibliotecas COFF (. lib), archivos objeto (. obj) de formato de modelo de objetos de 32 bits (OMF)|
|Extraer un miembro con/EXTRACT|Biblioteca COFF (. lib)|
|Compilar un archivo de exportación y una biblioteca de importación con/DEF|Archivo de definición de módulo (. def), archivos de objeto COFF (. obj), bibliotecas COFF (. lib), archivos de objeto OMF de 32 bits (. obj)|

> [!NOTE]
>  Las bibliotecas OMF creadas por la versión de 16 bits de LIB no se pueden usar como entrada para la versión de 32 bits de LIB.

## <a name="see-also"></a>Consulte también

[Información general sobre LIB](overview-of-lib.md)

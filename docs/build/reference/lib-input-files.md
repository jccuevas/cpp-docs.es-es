---
title: Archivos de entrada de LIB
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: de81f79eecf3fc73c02894747f4b97cb107cf892
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328228"
---
# <a name="lib-input-files"></a>Archivos de entrada de LIB

Los archivos de entrada esperados por LIB dependen del modo en el que se está utilizando, como se muestra en la tabla siguiente.

|Mode|Entrada|
|----------|-----------|
|Predeterminado (crear o modificar una biblioteca)|Archivos de objetoCOFF (.obj), bibliotecas COFF (.lib), archivos de objeto de formato de modelo de objetos de 32 bits (OMF) (.obj)|
|Extraer un miembro con /EXTRACT|Biblioteca COFF (.lib)|
|Creación de un archivo de exportación e biblioteca de importación con /DEF|Archivo de definición de módulo (.def), archivos de objetoCOFF (.obj), bibliotecas COFF (.lib), archivos de objeto OMF de 32 bits (.obj),|

> [!NOTE]
> Las bibliotecas OMF creadas por la versión de 16 bits de LIB no se pueden utilizar como entrada para la versión de 32 bits de LIB.

## <a name="see-also"></a>Consulte también

[Información general sobre LIB](overview-of-lib.md)

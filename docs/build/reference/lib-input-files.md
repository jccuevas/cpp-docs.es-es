---
title: Archivos de entrada de LIB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 952c3345234192e3798fea483d527cd3afec4bff
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702473"
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
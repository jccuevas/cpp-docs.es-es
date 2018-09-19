---
title: Archivos de resultados LIB | Microsoft Docs
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
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23665897266bab87c71b8b3889688113fe8aa99a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720712"
---
# <a name="lib-output-files"></a>Archivos de resultados de LIB

Los archivos de salida generados por LIB dependen del modo en el que se esté utilizando, tal como se muestra en la tabla siguiente.

|Modo|Salida|
|----------|------------|
|Predeterminado (generar o modificar una biblioteca)|Biblioteca COFF (.lib)|
|Extraer a un miembro con/Extract|Archivo objeto (.obj)|
|Creación de una exportación de archivo e importar biblioteca con la opción /DEF|Biblioteca de importación (.lib) y archivo de exportación (.exp)|

## <a name="see-also"></a>Vea también

[Información general sobre LIB](../../build/reference/overview-of-lib.md)
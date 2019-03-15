---
title: Archivos de entrada de LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 648871464dbc99972b8ca40579046347727e81cf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808136"
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

[Información general sobre LIB](overview-of-lib.md)

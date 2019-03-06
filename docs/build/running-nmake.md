---
title: Ejecutar NMAKE
ms.date: 09/05/2018
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: 1d3555dc66ba9939ce346a692df9d0151fcf87d2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423084"
---
# <a name="running-nmake"></a>Ejecutar NMAKE

## <a name="syntax"></a>Sintaxis

> **NMAKE** [*opción* ...] [*macros* ...] [*destinos* ...] [**\@**<em>/commandfile</em> ...]

## <a name="remarks"></a>Comentarios

Las compilaciones NMAKE solo especificadas *destinos* o, si se especifica ninguno, el primer destino en el archivo MAKE. El primer destino de archivo MAKE puede ser un [pseudodestino](../build/pseudotargets.md) que genera otros destinos. NMAKE utiliza archivos MAKE especificados con/f; Si no se especifica/f, utiliza el archivo MAKE en el directorio actual. Si no se especifica ningún archivo MAKE, utiliza reglas de inferencia para compilar la línea de comandos *destinos*.

El */commandfile* archivo de texto (o archivo de respuesta) contiene entradas de la línea de comandos. Otras entradas pueden ir precedidas o seguidas \@ */commandfile*. Se permite una ruta de acceso. En */commandfile*, saltos de línea se tratan como espacios. Escriba las definiciones de macro entre comillas si contienen espacios.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Opciones de NMAKE](../build/nmake-options.md)

[Tools.ini y NMAKE](../build/tools-ini-and-nmake.md)

[Códigos de salida de NMAKE](../build/exit-codes-from-nmake.md)

## <a name="see-also"></a>Vea también

[Referencia de NMAKE](../build/nmake-reference.md)

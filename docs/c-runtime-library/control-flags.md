---
title: Marcas de control
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
ms.openlocfilehash: 7ac5f239ea4d242618fb23ba617a3a6539492053
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750119"
---
# <a name="control-flags"></a>Marcas de control

La versión de depuración de la biblioteca en tiempo de ejecución de Microsoft c utiliza las siguientes marcas para controlar el proceso de creación de informes y asignación del montón. Para obtener más información, consulte [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).

|Marcar|Descripción|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Asigna las funciones del montón base a sus homólogos de la versión de depuración.|
|[_DEBUG](../c-runtime-library/debug.md)|Habilita el uso de las versiones de depuración de las funciones en tiempo de ejecución.|
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Controla cómo el administrador del montón de depuración hace un seguimiento de las asignaciones.|

Estas marcas se pueden definir con una opción de línea de comandos /D o con una directiva `#define`. Cuando se define la marca con `#define`, la directiva debe aparecer antes de la instrucción de inclusión del archivo de encabezado para las declaraciones rutinarias.

## <a name="see-also"></a>Vea también

[Variables globales y tipos estándar](../c-runtime-library/global-variables-and-standard-types.md)

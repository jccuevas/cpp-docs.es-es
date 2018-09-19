---
title: Marcas de control | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 716e597be5d337d11d58df944bbba468e496f078
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078067"
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
---
title: RUNTIME_FUNCTION (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f3831dc36664c556cf0a020ed87c60200443fd3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718242"
---
# <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION (Estructura)

Control de excepciones basado en tabla requiere una entrada de tabla para todas las funciones que asignan el espacio de pila o llamar a otra función (por ejemplo, las funciones de hoja). Entradas de la tabla de función tienen el formato:

|||
|-|-|
|ULONG|Dirección de inicio de la función|
|ULONG|Dirección final de la función|
|ULONG|Dirección de la información de desenredo|

La estructura RUNTIME_FUNCTION debe ser DWORD alineada en memoria. Todas las direcciones son relativas a imágenes, es decir, son desplazamientos de 32 bits de la dirección inicial de la imagen que contiene la entrada de la tabla de función. Estas entradas se ordenan y se colocan en la sección .pdata de una imagen PE32 +. Para funciones generadas dinámicamente [compiladores JIT], el tiempo de ejecución para admitir estas funciones debe usar RtlInstallFunctionTableCallback o RtlAddFunctionTable para proporcionar esta información para el sistema operativo. Si no lo hace se producirá en poco confiables control de excepciones y depuración de procesos.

## <a name="see-also"></a>Vea también

[Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)
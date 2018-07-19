---
title: RUNTIME_FUNCTION (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: 3c2f28380d4a14cf7617653ede20468c45649a8b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379931"
---
# <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION (Estructura)
Control de excepciones basado en tabla requiere una entrada de la tabla para todas las funciones que asignan espacio de pila o llamar a otra función (por ejemplo, funciones de hoja). Entradas de la tabla de función tienen el formato:  
  
|||  
|-|-|  
|ULONG|Dirección de inicio (función)|  
|ULONG|Dirección final (función)|  
|ULONG|Dirección de información de desenredo|  
  
 La estructura RUNTIME_FUNCTION debe ser DWORD alineada en memoria. Todas las direcciones son relativas a imágenes, es decir, son desplazamientos de 32 bits de la dirección inicial de la imagen que contiene la entrada de la tabla de función. Estas entradas se ordenan y se colocan en la sección .pdata de una imagen PE32 +. Para funciones generadas dinámicamente [compiladores JIT], el tiempo de ejecución para admitir estas funciones debe usar RtlInstallFunctionTableCallback o RtlAddFunctionTable para proporcionar esta información para el sistema operativo. Si no lo hace producirá confiable control de excepciones y depuración de procesos.  
  
## <a name="see-also"></a>Vea también  
 [Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)
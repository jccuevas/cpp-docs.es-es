---
title: RUNTIME_FUNCTION (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c05dcd516af5c078b4e4e664bae16f65370ca117
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
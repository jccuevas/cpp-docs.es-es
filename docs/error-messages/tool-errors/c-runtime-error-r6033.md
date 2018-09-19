---
title: C Runtime Error R6033 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6033
dev_langs:
- C++
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb107dcd2bd044ad6fb933869319bb7afd5aab72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049805"
---
# <a name="c-runtime-error-r6033"></a>C Runtime Error R6033

Intento de utilizar código MSIL de este ensamblado durante la inicialización del código nativo. Esto indica un error en la aplicación. Lo más probable es que es el resultado de una llamada a una compilación de MSIL (/ clr) función desde un constructor nativo o desde DllMain.

> [!NOTE]
>  Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Este error puede deberse a un error en la aplicación, o a un error en un complemento o una extensión que utiliza.
>
>  Puede intentar seguir estos pasos para corregir este error:
>
>  -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para quitar, reparar o reinstalar las extensiones o complementos.
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este diagnóstico indica que se estaban ejecutando instrucciones MSIL durante el bloqueo del cargador. Esto puede ocurrir si ha compilado C++ nativo mediante el indicador/CLR. Utilice solamente el indicador/CLR en módulos que contienen código administrado. Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).
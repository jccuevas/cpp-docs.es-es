---
title: R6019 de Error de tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95950254d4a0611d9690b8636eb50f2fc1f0f264
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314234"
---
# <a name="c-runtime-error-r6019"></a>R6019 de Error de tiempo de ejecución de C
no se puede abrir el dispositivo de consola  
  
> [!NOTE]
>  Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque intentó obtener acceso a la consola, pero no tiene permisos suficientes. Hay varias razones posibles para este error, pero suele ser porque se debe ejecutar el programa como administrador, o hay un error en el programa.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Ejecute el programa como administrador.  
> -   Use la **aplicaciones y características** o **programas y características** página en el **el Panel de Control** para reparar o reinstalar el programa.  
> -   Comprobar **Windows Update** en el **el Panel de Control** las actualizaciones de software.  
> -   Busque una versión actualizada de la aplicación. Si el problema continúa, póngase en contacto con el proveedor de la aplicación.  
  
 **Información para programadores**  
  
 Este error se produce porque la aplicación llamó a una función de la consola, pero el sistema operativo no haya concedido acceso a la consola. Excepto en el modo de depuración, consola generalmente no se permiten funciones en las aplicaciones de Microsoft Store. Si su aplicación requiere privilegios de administrador para que se ejecute, asegúrese de que está instalado para ejecutarse como administrador de forma predeterminada.
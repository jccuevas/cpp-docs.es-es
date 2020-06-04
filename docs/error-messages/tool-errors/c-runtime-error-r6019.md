---
title: Error en tiempo de ejecución de C R6019
ms.date: 11/04/2016
f1_keywords:
- R6019
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
ms.openlocfilehash: b647825b7e856be9dc51a5a652be87a4cc6d0e23
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197267"
---
# <a name="c-runtime-error-r6019"></a>Error en tiempo de ejecución de C R6019

no se puede abrir el dispositivo de consola

> [!NOTE]
> Si aparece este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque intentó acceder a la consola, pero no tenía permisos suficientes. Hay varias razones posibles para este error, pero suele deberse a que el programa debe ejecutarse como administrador o a que hay un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Ejecute el programa como administrador.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce porque la aplicación llamó a una función de consola, pero el sistema operativo no concedió acceso a la consola. Excepto en el modo de depuración, las funciones de consola generalmente no se permiten en Microsoft Store aplicaciones. Si la aplicación requiere privilegios de administrador para ejecutarse, asegúrese de que está instalado para ejecutarse como administrador de forma predeterminada.

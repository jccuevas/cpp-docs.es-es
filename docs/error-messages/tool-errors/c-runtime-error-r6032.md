---
title: Error en tiempo de ejecución de C R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: b29b946d08cff903cf0ca398ba0d7589cb5d54ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197098"
---
# <a name="c-runtime-error-r6032"></a>Error en tiempo de ejecución de C R6032

No hay espacio suficiente para la información de configuración regional

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo se debe a una condición de memoria extremadamente baja o a un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

El tiempo de ejecución mantiene información acerca de la configuración regional en cada subproceso para que pueda procesar las llamadas a funciones que dependen de la configuración regional. Si se produce un error en la asignación de memoria para esta información, el tiempo de ejecución no puede continuar porque hay demasiadas funciones básicas que dependen de ella.

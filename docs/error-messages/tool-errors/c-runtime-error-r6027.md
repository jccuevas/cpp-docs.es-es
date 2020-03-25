---
title: Error en tiempo de ejecución de C R6027
ms.date: 11/04/2016
f1_keywords:
- R6027
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
ms.openlocfilehash: 8c2aab7b090dbfa4553b8d1622f13aef13f58aa3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197176"
---
# <a name="c-runtime-error-r6027"></a>Error en tiempo de ejecución de C R6027

no hay espacio suficiente para la inicialización de lowio

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero normalmente se debe a una condición de memoria extremadamente baja. También puede deberse a un error en la aplicación, a daños en las bibliotecas visuales C++ que usa o a un controlador.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Si la aplicación estaba funcionando antes de una instalación reciente de otra aplicación o controlador, use la página **aplicaciones y características** o **programas y características** del **Panel de control** para quitar la nueva aplicación o el controlador y vuelva a intentar la aplicación.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar todas las copias del paquete redistribuible de Microsoft Visual. C++
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce cuando no hay suficiente memoria libre disponible para inicializar la compatibilidad de e/s de bajo nivel en el tiempo de ejecución de C. Este error suele producirse en el inicio de la aplicación. Compruebe que la aplicación y los controladores y los archivos DLL que se cargan no dañan el montón en el inicio.

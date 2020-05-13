---
title: Cambios en la función del asistente de carga retrasada de DLL desde Visual C++ 6.0
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 536729e27c89d068957ea451355957e4a35348ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320609"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Cambios en la función del asistente de carga retrasada de DLL desde Visual C++ 6.0

Si tiene varias versiones de Visual C++ en el equipo o si definió su propia función auxiliar, puede verse afectado por los cambios realizados en la función auxiliar de carga retrasada de DLL. Por ejemplo:

- **__delayLoadHelper** está **__delayLoadHelper2**

- **__pfnDliNotifyHook** está **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** está **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL ya** está **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> Si está utilizando la función auxiliar predeterminada, estos cambios no le afectarán. No hay cambios con respecto a cómo se invoca el vinculador.

## <a name="multiple-versions-of-visual-c"></a>Múltiples versiones de Visual C++

Si tiene varias versiones de Visual C++ en el equipo, asegúrese de que el vinculador coincida con delayimp.lib. Si hay una discordancia, obtendrá un error `___delayLoadHelper2@8` `___delayLoadHelper@8` del vinculador que informa o como un símbolo externo no resuelto. El primero implica un nuevo vinculador con un antiguo delayimp.lib, y el segundo implica un viejo vinculador con un nuevo delayimp.lib.

Si obtiene un error de vinculador sin resolver, ejecute [dumpbin /linkermember](linkermember.md):1 en delayimp.lib que espera contener la función auxiliar para ver qué función auxiliar se define en su lugar. La función auxiliar también se puede definir en un archivo de objeto; ejecute [dumpbin /symbols](symbols.md) `delayLoadHelper(2)`y busque .

Si sabe que tiene el vinculador Visual C++ 6.0, entonces:

- Ejecute dumpbin en el archivo .lib o .obj de la aplicación auxiliar de carga de retardo para determinar si define **__delayLoadHelper2**. Si no es así, el enlace fallará.

- Defina **__delayLoadHelper** en el archivo .lib o .obj de la aplicación auxiliar de carga de retardo.

## <a name="user-defined-helper-function"></a>Función auxiliar definida por el usuario

Si definió su propia función auxiliar y está utilizando la versión actual de Visual C++, haga lo siguiente:

- Cambie el nombre de la función auxiliar a **__delayLoadHelper2**.

- Puesto que los punteros en el descriptor de retardo (ImgDelayDescr en delayimp.h) se han cambiado de direcciones absolutas (VA) a direcciones relativas (RVA) para trabajar según lo esperado en programas de 32 y 64 bits, debe convertirestos de nuevo en punteros. Se ha introducido una nueva función: PFromRva, que se encuentra en delayhlp.cpp. Puede utilizar esta función en cada uno de los campos del descriptor para convertirlos de nuevo en punteros de 32 o 64 bits. La función auxiliar de carga de retardo predeterminada sigue siendo una buena plantilla para usar como ejemplo.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Cargar todas las importaciones para un archivo DLL cargado con retraso

El vinculador puede cargar todas las importaciones desde un archivo DLL que especificó que se cargarán con retraso. Consulte [Carga de todas las importaciones para un archivo DLL cargado](loading-all-imports-for-a-delay-loaded-dll.md) con retraso para obtener más información.

## <a name="see-also"></a>Consulte también

[Descripción de la función auxiliar](understanding-the-helper-function.md)

---
title: Cambios en la función del asistente de carga retrasada de DLL desde Visual C++ 6.0
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 8d50962bf66e07d6238be4a1a973c9d9ff06a556
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613777"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Cambios en la función del asistente de carga retrasada de DLL desde Visual C++ 6.0

Si tiene varias versiones de Visual C++ en el equipo o si ha definido una función auxiliar personalizada, puede verse afectado por los cambios realizados en el archivo DLL de carga retrasada función auxiliar. Por ejemplo:

- **__delayLoadHelper** es ahora **__delayLoadHelper2**

- **__pfnDliNotifyHook** es ahora **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** es ahora **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL** es ahora **__FUnloadDelayLoadedDLL2**

> [!NOTE]
>  Si utiliza la función auxiliar predeterminada, estos cambios no afectarán le. No hay ningún cambio con respecto a cómo se invoca el vinculador.

## <a name="multiple-versions-of-visual-c"></a>Varias versiones de Visual C++

Si tiene varias versiones de Visual C++ en el equipo, asegúrese de que el vinculador coincide con delayimp.lib. Si se produce un error de coincidencia, obtendrá un error del vinculador cualquiera `___delayLoadHelper2@8` o `___delayLoadHelper@8` como un símbolo externo sin resolver. El primero implica a un vinculador nuevo con una versión anterior de delayimp.lib, y el segundo implica a un vinculador antiguo con una versión nueva de delayimp.lib.

Si se produce un error de vinculador sin resolver, ejecute [dumpbin /linkermember](../../build/reference/linkermember.md): 1 en el archivo delayimp.lib que espera que contenga la función auxiliar para ver qué función auxiliar se define en su lugar. La función auxiliar también se podría definir en un archivo objeto; ejecute [dumpbin /symbols](../../build/reference/symbols.md) y busque `delayLoadHelper(2)`.

Si sabe que tiene, a continuación, el vinculador de Visual C++ 6.0:

- Ejecute dumpbin en archivo .lib o .obj el auxiliar de carga retrasada para determinar si define **__delayLoadHelper2**. Si no es así, se producirá un error en el vínculo.

- Definir **__delayLoadHelper** el retardo de cargar el archivo .lib o .obj de la aplicación auxiliar.

## <a name="user-defined-helper-function"></a>Función auxiliar definido por el usuario

Si define una función auxiliar personalizada y usa la versión actual de Visual C++, realice lo siguiente:

- Cambiar el nombre de la función auxiliar que **__delayLoadHelper2**.

- Puesto que los punteros en el descriptor de retraso (ImgDelayDescr en delayimp.h) se cambió de direcciones absolutas (VAs) a direcciones relativas (RVA) funcionen según lo previsto en ambos programas de 32 y 64 bits, deberá convertirlos de nuevo en punteros. Se ha introducido una nueva función: PFromRva, ubicada en delayhlp.cpp. Puede usar esta función en cada uno de los campos del descriptor para convertirlos a ambos punteros de 32 o 64 bits. La función de aplicación auxiliar de carga de retraso predeterminado sigue siendo una buena plantilla que usaremos como ejemplo.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Cargar todas las importaciones para un archivo DLL de carga retrasada

El vinculador puede cargar todas las importaciones desde un archivo DLL que especificó para la carga retrasada. Consulte [cargar todas las importaciones para un archivo DLL de carga retrasada](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md) para obtener más información.

## <a name="see-also"></a>Vea también

[Descripción de la función auxiliar](understanding-the-helper-function.md)
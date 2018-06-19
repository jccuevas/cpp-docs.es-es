---
title: Cambios en el archivo DLL de carga retrasan función auxiliar desde Visual C++ 6.0 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3af68e5ba92a96502e295e75520cd182b4633dae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371858"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Cambios en la función auxiliar de carga retrasada de DLL desde Visual C++ 6.0
Si tiene varias versiones de Visual C++ en el equipo o si ha definido una función auxiliar personalizada, es podrán que tenga problemas con los cambios realizados en el archivo DLL de carga retrasan función auxiliar. Por ejemplo:  
  
-   **__delayLoadHelper** es ahora **__delayLoadHelper2**  
  
-   **__pfnDliNotifyHook** es ahora **__pfnDliNotifyHook2**  
  
-   **__pfnDliFailureHook** es ahora **__pfnDliFailureHook2**  
  
-   **__FUnloadDelayLoadedDLL** es ahora **__FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  Si está utilizando la función auxiliar predeterminada, estos cambios no le afectarán. No hay ningún cambio con respecto a cómo invocar al vinculador.  
  
## <a name="multiple-versions-of-visual-c"></a>Varias versiones de Visual C++  
 Si tiene varias versiones de Visual C++ en el equipo, asegúrese de que el vinculador coincide con delayimp.lib. Si se produce un error de coincidencia, obtendrá un error del vinculador reporting cualquiera `___delayLoadHelper2@8` o `___delayLoadHelper@8` como un símbolo externo sin resolver. El primero implica a un vinculador nuevo con una versión anterior de delayimp.lib, y el segundo implica a un vinculador antiguo con una versión nueva de delayimp.lib.  
  
 Si recibe un error de vinculador sin resolver, ejecute [dumpbin /linkermember](../../build/reference/linkermember.md): 1 en el archivo delayimp.lib que espera que contenga la función auxiliar para ver qué función auxiliar se define en su lugar. La función auxiliar también se podría definir en un archivo objeto; ejecutar [dumpbin /symbols](../../build/reference/symbols.md) y busque `delayLoadHelper(2)`.  
  
 Si sabe que tiene el vinculador de Visual C++ 6.0, a continuación:  
  
-   Ejecute dumpbin en el archivo .lib o .obj de la auxiliar de carga retrasada para determinar si éste define **__delayLoadHelper2**. De lo contrario, se producirá un error en el vínculo.  
  
-   Definir **__delayLoadHelper** el retardo de cargar el archivo .lib o .obj del Ayudante.  
  
## <a name="user-defined-helper-function"></a>Función auxiliar definida por el usuario  
 Si define una función auxiliar personalizada y usa la versión actual de Visual C++, haga lo siguiente:  
  
-   Cambiar el nombre de la función auxiliar para **__delayLoadHelper2**.  
  
-   Puesto que los punteros en el descriptor de retraso (ImgDelayDescr en delayimp.h) se han cambiado de direcciones absolutas (VAs) para direcciones relativas (RVA) funcionen según lo previsto en ambos programas de 32 y 64 bits, debe convertirlos de nuevo en punteros. Se ha introducido una nueva función: PFromRva, ubicada en delayhlp.cpp. Puede utilizar esta función en cada uno de los campos del descriptor para convertirlos a ambos punteros de 32 bits o de 64 bits. La función de aplicación auxiliar de carga de retraso predeterminado sigue siendo una buena plantilla para usarla como un ejemplo.  
  
## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Cargar todas las importaciones para un archivo DLL de carga retrasada  
 El vinculador puede cargar todas las importaciones desde un archivo DLL que especificó para la carga retrasada. Vea [cargar todas las importaciones para un archivo DLL de carga retrasada](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Descripción de la función auxiliar](understanding-the-helper-function.md)
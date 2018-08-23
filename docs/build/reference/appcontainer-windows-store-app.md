---
title: /APPCONTAINER (aplicación de UWP/Microsoft Store) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eab6a9bd8ac37dec250739e3554c370726dce9eb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589582"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER (aplicación de Microsoft Store)
Especifica si el vinculador crea una imagen ejecutable que se debe ejecutar en un contenedor de aplicaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, /APPCONTAINER está desactivado.  
  
 Esta opción modifica un archivo ejecutable para indicar si se debe ejecutar la aplicación en el entorno de aislamiento de proceso appcontainer. Especifique /APPCONTAINER para una aplicación que se debe ejecutar en el entorno de appcontainer, por ejemplo, una aplicación de 8.x plataforma Universal de Windows (UWP) o Windows Phone. (La opción se establece automáticamente en Visual Studio cuando se crea una aplicación Windows Universal desde una plantilla.) Para una aplicación de escritorio, especifique/appcontainer: no o simplemente omita la opción.  
  
 La opción /APPCONTAINER se introdujo en Windows 8.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **línea de comandos** página de propiedades.  
  
5.  En **opciones adicionales**, escriba `/APPCONTAINER` o `/APPCONTAINER:NO`.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)
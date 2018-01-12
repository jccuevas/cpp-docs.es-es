---
title: "-APPCONTAINER (aplicación de la tienda de Windows) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22ca7bec885f20518950626d33f7e3af553d0d52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="appcontainer-windows-store-app"></a>/APPCONTAINER (aplicación de la Tienda Windows)
Especifica si el vinculador crea una imagen ejecutable que se debe ejecutar en un contenedor de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, /APPCONTAINER está desactivada.  
  
 Esta opción modifica un archivo ejecutable para indicar si se debe ejecutar la aplicación en el entorno de aislamiento de proceso appcontainer. Especificar /APPCONTAINER para una aplicación que se debe ejecutar en el entorno de appcontainer: por ejemplo, un [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] aplicación. (La opción se establece automáticamente en Visual Studio cuando se crea un [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] aplicación desde una plantilla.) Para una aplicación de escritorio, especifique /APPCONTAINER:NO o simplemente omite la opción.  
  
 La opción /APPCONTAINER se introdujo en [!INCLUDE[win8](../../build/reference/includes/win8_md.md)].  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **línea de comandos** página de propiedades.  
  
5.  En **opciones adicionales**, escriba `/APPCONTAINER` o `/APPCONTAINER:NO`.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)
---
title: Editor binario | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.binary.F1
dev_langs: C++
helpviewer_keywords:
- editors, Binary
- resources [Visual Studio], editing
- resource editors, Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4dade674fb32615e23904e6dbaf03d6c6ee0a371
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="binary-editor"></a>Editor binario
> [!WARNING]
>  El Editor binario no está disponible en las ediciones Express.  
  
 El Editor binario permite editar cualquier recurso, a nivel binario, en formato ASCII o hexadecimal. También se puede utilizar el [comando Buscar](/visualstudio/ide/reference/find-command) para buscar cadenas ASCII o bytes hexadecimales. Solo se debe utilizar el Editor binario cuando sea necesario ver o realizar pequeños cambios en recursos personalizados o en tipos de recursos no admitidos en el entorno de Visual Studio.  
  
 Para abrir el Editor binario, elija **archivo &#124; Nuevo &#124; Archivo** en el menú principal, seleccione el archivo que desee editar y, después, haga clic en la flecha desplegable situada junto a la **abiertos** botón y elija **abrir con &#124; Editor binario**.  
  
> [!CAUTION]
>  Es peligroso editar recursos como cuadros de diálogo, imágenes o menús en el Editor binario. Una edición incorrecta podría dañar el recurso y hacerlo ilegible en su editor nativo.  
  
> [!TIP]
>  Cuando se trabaja en el Editor binario, en muchos casos es posible hacer clic con el botón secundario para abrir un menú contextual de comandos específicos de un recurso. Los comandos disponibles dependen del objeto al que apunta el cursor. Por ejemplo, si se hace clic mientras se apunta al Editor binario teniendo seleccionados valores hexadecimales, el menú contextual muestra los comandos **Cortar**, **Copiar**y **Pegar** .  
  
 Con el Editor binario, se puede hacer lo siguiente:  
  
-   [Abrir un recurso para editarlo en modo binario](../windows/opening-a-resource-for-binary-editing.md)  
  
-   [Editar datos binarios](../windows/editing-binary-data.md)  
  
-   [Buscar datos binarios](../windows/finding-binary-data.md)  
  
-   [Crear un nuevo recurso personalizado o de datos](../windows/creating-a-new-custom-or-data-resource.md)  
  
## <a name="managed-resources"></a>Recursos administrados  
 Se puede utilizar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el Editor binario para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Editores de recursos](../windows/resource-editors.md)


---
title: Agregar una propiedad (Visual C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33fc8c3b5528c0ced4e0d402aec48791b7fbcb9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-property-visual-c"></a>Agregar una propiedad (Visual C++)
Puede usar el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md) para agregar un método a una interfaz en el proyecto.  
  
### <a name="to-add-a-property-to-your-object"></a>Para agregar una propiedad al objeto  
  
1.  En [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic en el nombre de la interfaz a la que desea agregar la propiedad.  
  
    > [!NOTE]
    >  También puede agregar propiedades a interfaces dispinterface, que, a menos que el proyecto tenga atributos, está anidado dentro del nodo de biblioteca.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar propiedad**.  
  
3.  En el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md), proporcione la información para crear la propiedad.  
  
4.  Especifique cualquier configuración de idioma (IDL) de la definición de interfaz para la propiedad en el [atributos IDL](../ide/idl-attributes-add-property-wizard.md) página del asistente.  
  
5.  Haga clic en **finalizar** para agregar la propiedad.  
  
 El **obtener** y `Put` se muestran los métodos de la propiedad como dos iconos en vista de clases, bajo la interfaz donde se haya definido. Hacer doble clic en cualquiera de los iconos para ver la declaración de propiedad en el archivo IDL.  
  
-   Para las interfaces ATL, la **obtener** y **colocar** funciones se agregan al archivo .cpp y archivo .h se agregan referencias a estas funciones.  
  
-   Para interfaces dispinterface MFC, si selecciona **variable miembro** como el tipo de implementación, un método y una variable se agregan a la clase que lo implementa. Si selecciona **métodos Get/Set** como el tipo de implementación, se agregan dos métodos a la clase que lo implementa.  
  
## <a name="see-also"></a>Vea también  
 [Crear una interfaz COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Editar una interfaz COM](../ide/editing-a-com-interface.md)   
 [El modelo de objetos componentes](http://msdn.microsoft.com/library/windows/desktop/ms694363)   
 [Punteros de interfaz e Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms688484)
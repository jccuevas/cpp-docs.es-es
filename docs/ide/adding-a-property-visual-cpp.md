---
title: Agregar una propiedad (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45eda098202fdf9286905bdc967b6aa1d7bd7035
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327585"
---
# <a name="adding-a-property-visual-c"></a>Agregar una propiedad (Visual C++)
Se puede usar el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md) para agregar un método a una interfaz en el proyecto.  
  
### <a name="to-add-a-property-to-your-object"></a>Para agregar una propiedad al objeto  
  
1.  En la [Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón derecho en la interfaz a la que quiera agregar la propiedad.  
  
    > [!NOTE]
    >  También puede agregar propiedades a interfaces dispinterface que, a menos que el proyecto tenga atributos, se anidan bajo el nodo de biblioteca.  
  
2.  En el menú contextual, haga clic en **Agregar** y después en **Agregar propiedad**.  
  
3.  En el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md), proporcione la información para crear la propiedad.  
  
4.  Especifique cualquier configuración de lenguaje de definición de interfaz (IDL) para la propiedad en la página [Atributos IDL](../ide/idl-attributes-add-property-wizard.md) del asistente.  
  
5.  Haga clic en **Finalizar** para agregar la propiedad.  
  
 Los métodos **Get** y `Put` de la propiedad se muestran como dos iconos en la Vista de clases, bajo la interfaz donde se haya definido. Puede hacer doble clic en cualquiera de los iconos para ver la declaración de propiedad en el archivo .idl.  
  
-   Para las interfaces ATL, las funciones **Get** y **Put** se agregan al archivo .cpp, y las referencias a estas funciones se agregan al archivo .h.  
  
-   Para las interfaces dispinterface de MFC, si selecciona **Variable miembro** como el tipo de implementación, se agregan un método y una variable a la clase que lo implementa. Si selecciona **Métodos Get/Set** como el tipo de implementación, se agregan dos métodos a la clase que lo implementa.  
  
## <a name="see-also"></a>Vea también  
 [Crear una interfaz COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Editar una interfaz COM](../ide/editing-a-com-interface.md)   
 [The Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)  (Modelo de objetos componentes (COM))  
 [Interface Pointers and Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms688484) (Punteros de interfaz e interfaces)
---
title: 'Cómo: buscar símbolos en recursos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3040e89ee4c729953c1a56f0c8728ba4d5b9d7b6
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570527"
---
# <a name="how-to-search-for-symbols-in-resources"></a>Cómo: Buscar símbolos en recursos
### <a name="to-find-symbols-in-resources"></a>Para buscar símbolos en recursos:  
  
1.  Desde el **editar** menú, elija **Buscar símbolo**.  
  
2.  En el [cuadro de diálogo Buscar símbolo](http://msdn.microsoft.com/63e93d9c-784f-418d-a76a-723da5ff5d96), en el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba la tecla de aceleración que desea buscar (por ejemplo, ID_ACCEL1).  
  
    > [!TIP]
    >  Para usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) para la búsqueda, debe usar el [comando Buscar en archivos](/visualstudio/ide/reference/find-command) desde el **editar** menú en lugar de la **Buscar símbolo**comando. Para habilitar las expresiones regulares, debe tener la **uso: las expresiones regulares** casilla seleccionada en el [cuadro de diálogo Buscar](http://msdn.microsoft.com/dad03582-4931-4893-83ba-84b37f5b1600). Puede hacer clic en el botón de flecha derecha situada a la derecha de la **buscar** cuadro para mostrar una lista de expresiones regulares de búsqueda. Al seleccionar una expresión de esta lista, se usará como el texto de búsqueda en el **buscar** cuadro.  
  
3.  Seleccione cualquiera de los **buscar** opciones.  
  
4.  Haga clic en **Buscar siguiente**.  
  
    > [!NOTE]
    >  No se pueden buscar símbolos en los recursos binarios, de acelerador o de cadena.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. . Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)   
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)
---
title: "Agregar una entrada a una tabla de aceleradores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tablas de aceleradores [C++], agregar entradas"
  - "Nuevo acelerador (comando)"
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Agregar una entrada a una tabla de aceleradores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Para agregar una entrada a una tabla de aceleradores  
  
1.  Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Haga clic en la tabla de aceleradores y elija **Nuevo acelerador** en el menú contextual, o haga clic en la entrada de fila vacía en la parte inferior de la tabla.  
  
3.  Seleccione un [ID](Id%20Property.xml) en la lista desplegable en el Id. de cuadro o escriba un nuevo Id. de la **ID** cuadro.  
  
4.  Tipo de la [clave](../Topic/Accelerator%20Key%20Property.md) que desee utilizar como acelerador o con el botón secundario y elija **tecla siguiente** desde el menú contextual para definir una combinación de teclas (el **tecla siguiente** comando también está disponible desde el **Editar** menú).  
  
5.  Cambiar el [modificador](../windows/accelerator-modifier-property.md) y [tipo](../windows/accelerator-type-property.md), si es necesario.  
  
6.  Presione **ENTRAR**.  
  
    > [!NOTE]
    >  Asegúrese de que todos los aceleradores que defina sean únicos. Puede asignar varias combinaciones de teclas al mismo identificador sin que se produzcan efectos negativos; por ejemplo, CTRL+P y F8 pueden asignarse a ID_PRINT. Sin embargo, tener una combinación de teclas asignada a más de un identificador no funcionará bien; por ejemplo, CTRL+Z asignado tanto a ID_SPELL_CHECK como a ID_THESAURUS.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework* . Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos de**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editar tablas de aceleradores](../windows/editing-accelerator-tables.md)   
 [Editor de aceleradores](../mfc/accelerator-editor.md)
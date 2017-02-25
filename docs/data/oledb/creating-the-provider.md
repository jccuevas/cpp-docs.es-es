---
title: "Crear un proveedor | Microsoft Docs"
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
  - "proveedores OLE DB, crear"
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Crear un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

#### Para crear un proveedor OLE DB con el Asistente para proveedores OLE DB ATL  
  
1.  Haga clic con el botón secundario en el proyecto.  
  
2.  En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar clase**.  
  
3.  En el cuadro de diálogo **Agregar clase**, seleccione el icono **Proveedor OLE DB ATL** y, a continuación, haga clic en **Abrir**.  
  
4.  En el Asistente para proveedores OLE DB ATL, escriba un nombre corto para el proveedor en el cuadro **Nombre corto**.  En los temas siguientes se utiliza el nombre corto "MyProvider", pero se puede utilizar cualquier otro nombre.  Los otros cuadros de nombre se crean en función del nombre que escriba.  
  
5.  Modifique los otros cuadros de nombre, si es necesario.  Además de los nombres de objeto y de archivo, puede editar lo siguiente:  
  
    -   **Coclass**: nombre que utiliza COM para crear el proveedor.  
  
    -   **ProgID**: identificador de programación, una cadena de texto que se puede utilizar en lugar de un GUID.  
  
    -   **Versión**: se utiliza con los valores de ProgID y CoClass para generar un identificador para programación dependiente de la versión.  
  
6.  Haga clic en **Finalizar**.  
  
## Vea también  
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
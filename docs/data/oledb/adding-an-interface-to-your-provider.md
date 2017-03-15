---
title: "Agregar una interfaz a un proveedor | Microsoft Docs"
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
  - "plantillas del proveedor OLE DB, interfaces de objetos"
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Agregar una interfaz a un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determine qué objeto desea agregar a la interfaz \(normalmente, objetos de origen de datos, conjunto de filas, comando o sesión creados por el Asistente para proveedores OLE DB\).  Es posible que el objeto que desea agregar a la interfaz no sea compatible actualmente con el proveedor.  En ese caso, ejecute el Asistente para proveedores OLE DB ATL para crear el objeto.  En la Vista de clases, haga clic con el botón secundario del mouse en el proyecto, haga clic en **Agregar clase** en el menú **Agregar** y, a continuación, haga clic en **Proveedor OLE DB ATL**.  Es posible que desee colocar el código de la interfaz en un directorio independiente y después copiar los archivos al proyecto de proveedor.  
  
 Si creó una clase nueva para ofrecer compatibilidad con la interfaz, haga que el objeto herede de la clase.  Por ejemplo, podría agregar la clase **IRowsetIndexImpl** a un objeto de conjunto de filas:  
  
```  
template <class Creator>  
class CAgentRowset :   
public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
   public IRowsetIndexImpl< ... >   
```  
  
 Agregue la interfaz a **COM\_MAP** del objeto mediante la macro COM\_INTERFACE\_ENTRY.  Si no hay ningún mapa, créelo.  Por ejemplo:  
  
```  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
 Para el objeto de conjunto de filas, encadene el mapa del objeto primario, de forma que el objeto pueda delegar en la clase primaria.  En este ejemplo, agregue la macro COM\_INTERFACE\_ENTRY\_CHAIN al mapa:  
  
```  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
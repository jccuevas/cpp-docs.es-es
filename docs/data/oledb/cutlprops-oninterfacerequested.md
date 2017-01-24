---
title: "CUtlProps::OnInterfaceRequested | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CUtlProps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnInterfaceRequested (método)"
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps::OnInterfaceRequested
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Orden de los identificadores una interfaz opcional cuando un consumidor llama a un método en una de las interfaces de la creación de objetos.  
  
## Sintaxis  
  
```  
  
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(  
   REFIID riid  
);  
```  
  
#### Parámetros  
 `riid`  
 \[in\] El IID de la interfaz solicitada.  Para obtener más detalles, vea la descripción del parámetro de `riid` de `ICommand::Execute` en *la referencia del* programador \(en *el SDK de MDAC*\).  
  
## Comentarios  
 **OnInterfaceRequested** controla las solicitudes de consumidor una interfaz opcional cuando un consumidor llama a un método en una de las interfaces de creación de objeto \(como **IDBCreateSession**, **IDBCreateCommand**, `IOpenRowset`, o `ICommand`\).  Establece la propiedad correspondiente de OLE DB para la interfaz solicitada.  Por ejemplo, si el consumidor solicita **IID\_IRowsetLocate**, **OnInterfaceRequested** establece la interfaz de **DBPROP\_IRowsetLocate** .  Al hacer mantiene tan al estado correcto durante la creación del conjunto de filas.  
  
 Se llama a este método cuando el consumidor llama a **IOpenRowset::OpenRowset** o `ICommand::Execute`.  
  
 Si un usuario abre un objeto y solicita una interfaz opcional, el proveedor debe establecer la propiedad asociada a la interfaz a `VARIANT_TRUE`.  Para permitir el procesamiento propiedad\- concreto, **OnInterfaceRequested** se denomina antes de llamar al método de **Ejecución** del proveedor.  De forma predeterminada, **OnInterfaceRequested** controla las siguientes interfaces:  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 Si desea administrar otras interfaces, invalide esta función en el origen de datos, sesión, el comando, o la clase de conjunto de filas de procesar funciones.  El reemplazo debe realizar el determinado normal\/obtiene interfaces de propiedades para asegurarse de que establecer propiedades también establece todas las propiedades encadenada \(vea [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)\).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CUtlProps \(Clase\)](../../data/oledb/cutlprops-class.md)
---
title: "CDBPropSet::AddProperty | Microsoft Docs"
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
  - "CDBPropSet::AddProperty"
  - "CDBPropSet.AddProperty"
  - "AddProperty"
  - "ATL::CDBPropSet::AddProperty"
  - "ATL.CDBPropSet.AddProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddProperty (método)"
ms.assetid: dc9539d3-1ee4-40f3-9281-2068e6d65e93
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropSet::AddProperty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega una propiedad al conjunto de propiedades.  
  
## Sintaxis  
  
```  
  
      bool AddProperty(   
   DWORD dwPropertyID,   
   const VARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCSTR szValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCWSTR szValue,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   bool bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   BYTE bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   short nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   long nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   float fltValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   double dblValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   CY cyValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
```  
  
#### Parámetros  
 *dwPropertyID*  
 \[in\] El identificador de la propiedad que se va a agregar.  Se utiliza para inicializar **dwPropertyID** de la estructura de `DBPROP` agregada al conjunto de propiedades.  
  
 `var`  
 \[in\] Una variante que se utiliza para inicializar el valor de propiedad para la estructura de `DBPROP` agregada al conjunto de propiedades.  
  
 `szValue`  
 \[in\] Una cadena utilizada para inicializar el valor de propiedad para la estructura de `DBPROP` agregada al conjunto de propiedades.  
  
 `bValue`  
 \[in\] **byte** O un valor booleano que se utiliza para inicializar el valor de propiedad para la estructura de `DBPROP` agregada al conjunto de propiedades.  
  
 `nValue`  
 \[in\] Un valor entero utilizado para inicializar el valor de propiedad para la estructura de `DBPROP` agregada al conjunto de propiedades.  
  
 *fltValue*  
 \[in\] Un valor flotante utilizado para inicializar el valor de propiedad para la estructura de `DBPROP` agregada al conjunto de propiedades.  
  
 `dblValue`  
 \[in\] Un valor flotante de doble precisión utilizado para inicializar el valor de propiedad para la estructura de `DBPROP` agregada al conjunto de propiedades.  
  
 `cyValue`  
 \[in\] Un valor de divisa de CY utilizado para inicializar el valor de propiedad para la estructura de `DBPROP` agregada al conjunto de propiedades.  
  
## Valor devuelto  
 **true** si la propiedad se agregó correctamente.  De lo contrario, es **false**.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDBPropSet \(Clase\)](../../data/oledb/cdbpropset-class.md)   
 [DBPROP Structure](https://msdn.microsoft.com/en-us/library/ms717970.aspx)
---
title: "CRowsetImpl (Clase) | Microsoft Docs"
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
  - "CRowsetImpl"
  - "ATL.CRowsetImpl"
  - "ATL::CRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRowsetImpl (clase)"
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de conjunto de filas OLE DB sin requerir la herencia múltiple de las interfaces de implementación.  
  
## Sintaxis  
  
```  
template <  
   class T,  
   class Storage,  
   class CreatorClass,  
   class ArrayType = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class RowsetInterface = IRowsetImpl < T, IRowset >   
>  
class CRowsetImpl :    
   public CComObjectRootEx<CreatorClass::_ThreadModel>,   
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,   
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>  
```  
  
#### Parámetros  
 `T`  
 La clase de usuario que deriva de `CRowsetImpl`.  
  
 `Storage`  
 La clase de registro de usuario.  
  
 `CreatorClass`  
 La clase que contiene las propiedades para el conjunto de filas; normalmente el comando.  
  
 `ArrayType`  
 La clase que actuará como almacenamiento para los datos del conjunto de filas.  El valor predeterminado de este parámetro a `CAtlArray`, pero pueden ser cualquier clase que admite la funcionalidad necesaria.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|Dibuja una cadena de **DBID** y cópiela en `bstr` pasado.|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|Valida y almacena s para **DBID**en las dos cadenas \([m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)\).|  
  
### Métodos reemplazables  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/crowsetimpl-getcolumninfo.md)|Información de columna de recupera para una solicitud de cliente determinado.|  
|[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)|Comprueba si algún o ambos parámetros contienen valores de cadena, y si es así copias los valores de cadena a los miembros de datos [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
|[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)|Comprueba si algún o s para **DBID**contiene valores de cadena, y si es así los copian los miembros de datos [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|De forma predeterminada, `CAtlArray` que templatizes en el argumento de plantilla de registro de usuario a `CRowsetImpl`.  Otra clase de tipo de matriz puede utilizar cambiando el argumento de plantilla de `ArrayType` a `CRowsetImpl`.|  
|[m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|Contiene el comando inicial de conjunto de filas.|  
|[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|Contiene el índice inicial de conjunto de filas.|  
  
## Comentarios  
 `CRowsetImpl` proporciona reemplaza en forma de la conversión hacia arriba estáticas.  Los métodos controlan la manera en que un conjunto de filas especificado validará el texto de comando.  Puede crear dispone `CRowsetImpl`\- clases de estilo creando las interfaces de implementación múltiple\- heredadas.  El único método para el que debe proporcionar la implementación es **Ejecución**.  Dependiendo de lo que está creando el tipo de conjunto de filas se, el generador que los métodos contarán con firmas diferentes para **Ejecución**.  Por ejemplo, si utiliza `CRowsetImpl`\- clase derivada a implementar un conjunto de filas de esquema, el método de **Ejecución** tendrá la siguiente firma:  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 Si está creando `CRowsetImpl`\- clase derivada a implementar un conjunto de filas del comando o de sesión, el método de **Ejecución** tendrá la siguiente firma:  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 Para implementar `CRowsetImpl`cualquiera de los \- los métodos derivados de **Ejecución** , debe rellenar los búferes de datos internos \([m\_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)\).  
  
## Requisitos  
 **Header:** atldb.h
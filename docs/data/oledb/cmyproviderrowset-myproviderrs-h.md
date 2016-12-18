---
title: "CMyProviderRowset (MyProviderRS.H) | Microsoft Docs"
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
  - "cmyproviderrowset"
  - ""myproviderrs.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMyProviderRowset (clase): MyProviderRS.H"
  - "proveedores OLE DB, archivos generados por el asistente"
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderRowset (MyProviderRS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El asistente genera una entrada para el objeto de conjunto de filas.  En este caso, se denomina `CMyProviderRowset`.  La clase `CMyProviderRowset` hereda de una clase de proveedor OLE DB llamada `CRowsetImpl`, que implementa todas las interfaces necesarias para el objeto de conjunto de filas.  El siguiente fragmento de código muestra la cadena de herencia para `CRowsetImpl`:  
  
```  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T > >  
```  
  
 `CRowsetImpl` también utiliza las interfaces `IAccessor` e `IColumnsInfo`.  Utiliza estas interfaces para campos de resultados en las tablas.  La clase también proporciona una implementación para **IRowsetIdentity**, que permite al consumidor determinar si dos filas son idénticas.  La interfaz `IRowsetInfo` implementa propiedades para el objeto de conjunto de filas.  La interfaz **IConvertType** permite al proveedor resolver diferencias entre los tipos de datos solicitados por el consumidor y los utilizados por el proveedor.  
  
 La interfaz `IRowset` controla en realidad la recuperación de datos.  El consumidor llama primero a un método denominado `GetNextRows` para devolver un identificador a una fila, conocido como **HROW**.  Después llama a **IRowset::GetData** con ese identificador **HROW** para recuperar los datos solicitados.  
  
 `CRowsetImpl` también utiliza varios parámetros de plantilla.  Estos parámetros permiten determinar cómo controla los datos la clase `CRowsetImpl`.  El argumento `ArrayType` permite determinar el mecanismo de almacenamiento que se utiliza para almacenar los datos de la fila.  El parámetro **RowClass** especifica la clase que contiene un identificador **HROW**.  
  
 El parámetro **RowsetInterface** permite utilizar también las interfaces `IRowsetLocate` o `IRowsetScroll`.  Las interfaces `IRowsetLocate` e `IRowsetScroll` heredan desde `IRowset`.  Por tanto, las plantillas de proveedor OLE DB deben proporcionar un control especial para estas interfaces.  Si desea utilizar alguna de estas interfaces, debe utilizar este parámetro.  
  
## Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)
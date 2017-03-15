---
title: "Modificar la herencia de RMyProviderRowset | Microsoft Docs"
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
  - "herencia [C++]"
  - "RMyProviderRowset"
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Modificar la herencia de RMyProviderRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para agregar la interfaz `IRowsetLocate` al ejemplo de proveedor sencillo de sólo lectura, modifique la herencia de **RMyProviderRowset**.  Inicialmente, **RMyProviderRowset** hereda de `CRowsetImpl`.  Debe modificarla para que herede de **CRowsetBaseImpl**.  
  
 Para ello, cree una clase nueva, `CMyRowsetImpl`, en MyProviderRS.h:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate > >  
{  
...  
};  
```  
  
 Ahora, edite el mapa de la interfaz COM de MyProviderRS.h para convertirlo en el siguiente:  
  
```  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 De esta forma, se crea un mapa de interfaz COM que indica a `CMyRowsetImpl` que debe llamar a **QueryInterface**  para las interfaces `IRowset` e `IRowsetLocate`.  Para lograr la implementación completa de las clases de conjunto de filas, el mapa vincula la clase `CMyRowsetImpl` con la clase **CRowsetBaseImpl** definida por las Plantillas OLE DB; el mapa utiliza la macro COM\_INTERFACE\_ENTRY\_CHAIN, que indica a las plantillas OLE DB que deben analizar el mapa COM en **CRowsetBaseImpl** como respuesta a una llamada de `QueryInterface`.  
  
 Por último, vincule `RAgentRowset` a `CMyRowsetBaseImpl` modificando `RAgentRowset` de forma que herede de `CMyRowsetImpl`, de la manera siguiente:  
  
```  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset` puede utilizar ahora la interfaz `IRowsetLocate` a la vez que aprovecha el resto de la implementación de la clase de conjunto de filas.  
  
 Cuando haya hecho esto, puede [determinar dinámicamente las columnas que se devuelven al consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## Vea también  
 [Mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)
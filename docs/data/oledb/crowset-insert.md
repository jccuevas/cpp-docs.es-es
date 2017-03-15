---
title: "CRowset::Insert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset<TAccessor>.Insert"
  - "CRowset.Insert"
  - "CRowset<TAccessor>.Insert"
  - "CRowset<TAccessor>::Insert"
  - "ATL::CRowset<TAccessor>::Insert"
  - "ATL.CRowset.Insert"
  - "CRowset::Insert"
  - "ATL::CRowset::Insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Insert (método)"
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CRowset::Insert
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea e inicializa una nueva fila con datos de descriptor de acceso.  
  
## Sintaxis  
  
```  
  
      HRESULT Insert(   
   int nAccessor = 0,   
   bool bGetHRow = false    
) throw( );  
```  
  
#### Parámetros  
 `nAccessor`  
 \[in\] El número de descriptor de acceso para insertar datos.  
  
 *bGetHRow*  
 \[in\] Indica si el identificador para la fila insertada se recupera.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método requiere la interfaz opcional `IRowsetChange`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetChange** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
 Insert podría producir errores si una o más columnas no son programables.  Modifique el mapa de cursores para corregirlo.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo obtener acceso a un origen de datos a través de un conjunto de filas y luego insertar una cadena mediante una tabla en ese conjunto de filas.  
  
 Primero, cree una clase de tabla insertando un objeto New ATL en el proyecto.  Por ejemplo, haga clic con el botón secundario en el panel del área de trabajo y **New ATL Object**seleccione.  De la categoría de **Data Access** , seleccione **Consumidor**.  Cree un objeto consumidor de **Tabla**escrito. \(Seleccionar **Tabla** crea un conjunto de filas directamente de la tabla; seleccione **Comando** crea un conjunto de filas a través de un comando SQL\). Seleccione un origen de datos, especificando una tabla con el que para tener acceso a ese origen de datos.  Si llama al objeto **CCustomerTable**consumidor, después se aplicaría el código de inserción como sigue:  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/CPP/crowset-insert_1.cpp)]  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)
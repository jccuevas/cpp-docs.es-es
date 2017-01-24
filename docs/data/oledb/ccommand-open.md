---
title: "CCommand::Open | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CCommand.Open"
  - "ATL::CCommand::Open"
  - "CCommand.Open"
  - "CCommand::Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open (método)"
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ejecuta y enlaza opcionalmente el comando.  
  
## Sintaxis  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCWSTR wszCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   const CSession& session,  
   LPCSTR szCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   const CSession& session,  
   INT szCommand = NULL,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### Parámetros  
 `session`  
 \[in\] La sesión en la que se ejecuta el comando.  
  
 `wszCommand`  
 \[in\] El comando para ejecutarse, pasado como cadena Unicode.  Puede ser **nulo** al utilizar `CAccessor`, en este caso recuperar el comando del valor pasado a la macro de [DEFINE\_COMMAND](../../data/oledb/define-command.md) .  Vea [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) en *la referencia del* programador para obtener detalles.  
  
 `szCommand`  
 \[in\] Igual que `wszCommand` salvo que este parámetro toma una cadena de comando ANSI.  El cuarto formulario de este método puede tomar un valor nulo.  Vea “notas” más adelante en este tema para obtener detalles.  
  
 *pPropSet*  
 \[in\] Un puntero a una matriz de estructuras de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) que contienen las propiedades y los valores que se establecerán.  Vea [Conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/en-us/library/ms713696.aspx) en *la referencia del* programador de OLE [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `pRowsAffected`  
 \[in\/out\] Un puntero a la memoria donde el recuento de filas afectadas por un comando se devuelve.  Si *se \*pRowsAffected* es cambia **nulo**, ningún recuento de filas.  Si no, conjuntos de **Abierta** \*`pRowsAffected` según las condiciones siguientes:  
  
|Si|Entonces...|  
|--------|-----------------|  
|El elemento de **cParamSets** de `pParams` es mayor que 1|\*`pRowsAffected` representa el número total de filas afectadas por todos los conjuntos de parámetros especificados en la ejecución.|  
|El número de filas afectadas no está disponible|\*`pRowsAffected` se establece – 1.|  
|El comando no actualiza, eliminar, ni inserta filas|\*`pRowsAffected` es indefinido.|  
  
 `guidCommand`  
 \[in\] GUID que especifica la sintaxis y las reglas generales para que el proveedor usa de analizar el texto de comando.  Vea [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) y [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) en *la referencia del* programador para obtener detalles.  
  
 `bBind`  
 \[in\] Especifica si enlazar el comando automáticamente después de ejecutarse.  El valor predeterminado es **true**, que hace que el comando de enlazarse automáticamente.  El valor `bBind` a **false** evita el enlace automático del comando para que pueda enlazar manualmente. \(El enlace manual resulta especialmente interesante para los usuarios de OLAP\).  
  
 `ulPropSets`  
 \[in\] El número de estructuras de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) pasadas en el argumento *de pPropSet* .  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Los primeros tres formas de **Abierta** toman una sesión, crean un comando, y ejecuta el comando, enlazar cualquier parámetro según sea necesario.  
  
 El primer formulario de **Abierta** toma una cadena de comando Unicode y no tiene ningún valor predeterminado.  
  
 El segundo formato de **Abierta** toma una cadena de comando ANSI y ningún valor predeterminado \(proporcionados por compatibilidad con versiones anteriores las aplicaciones existentes de ANSI\).  
  
 El tercer formulario de **Abierta** permite que la cadena de comando sea NULL, debido a `int` escrito con un valor predeterminado de NULL.  Se proporciona para llamar a `Open(session, NULL);` o `Open(session);` porque NULL es de `int`escrito.  Esta versión requiere y afirma que el parámetro de `int` sea NULL.  
  
 Utilice el cuarto formulario de **Abierta** cuando haya creado un comando y desea realizar solo [Preparación](../../data/oledb/ccommand-prepare.md) y ejecuciones.  
  
> [!NOTE]
>  **Abierta** llama **Ejecución**, que a su vez llama a `GetNextResult`.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)
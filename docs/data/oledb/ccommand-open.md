---
title: 'CCommand:: Open | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13945181ac92ec35e0b252f31382202414333bc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ccommandopen"></a>CCommand::Open
Se ejecuta y, opcionalmente, enlaza el comando.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `session`  
 [in] La sesión en el que se va a ejecutar el comando.  
  
 `wszCommand`  
 [in] El comando se ejecute, se pasa como una cadena Unicode. Puede ser **NULL** al usar `CAccessor`, en cuyo caso se recuperará el comando desde el valor pasado a la [DEFINE_COMMAND](../../data/oledb/define-command.md) macro. Vea [ICommand:: Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) en el *referencia del programador de OLE DB* para obtener más información.  
  
 `szCommand`  
 [in] Igual que `wszCommand` salvo que este parámetro toma una cadena de comando de ANSI. La cuarta forma de este método puede tomar un valor NULL. Vea "Comentarios" más adelante en este tema para obtener más información.  
  
 *pPropSet*  
 [in] Un puntero a una matriz de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) las estructuras que contienen propiedades y valores que desea establecer. Vea [conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/en-us/library/ms713696.aspx) en el *referencia del programador OLE DB* en el SDK de Windows.  
  
 `pRowsAffected`  
 [los in/out] Un puntero a memoria que se devuelve el recuento de filas afectadas por un comando. Si  *\*pRowsAffected* es **NULL**, no se devuelve ningún recuento de filas. En caso contrario, **abiertos** establece *`pRowsAffected` según las condiciones siguientes:  
  
|Si|A continuación|  
|--------|----------|  
|El **cParamSets** elemento de `pParams` es mayor que 1|*`pRowsAffected`representa el número total de filas afectadas por todos los conjuntos de parámetros especificados en la ejecución.|  
|El número de filas afectadas no está disponible|*`pRowsAffected`se establece en -1.|  
|El comando no actualizar, eliminar o insertar filas|*`pRowsAffected`no está definido.|  
  
 `guidCommand`  
 [in] Un GUID que especifica la sintaxis y las reglas generales para el proveedor debe usar al analizar el texto del comando. Vea [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) y [ICommandText:: SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) en el *referencia del programador de OLE DB* para obtener más información.  
  
 `bBind`  
 [in] Especifica si se debe enlazar el comando automáticamente después de que se está ejecutando. El valor predeterminado es **true**, lo que hace que el comando enlazar automáticamente. Establecer `bBind` a **false** evita que el enlace automático del comando para que pueda enlazar manualmente. (Enlace manual es de particular interés para los usuarios OLAP).  
  
 `ulPropSets`  
 [in] El número de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) estructuras pasan en el *pPropSet* argumento.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Las primeras tres formas de **abiertos** tomar una sesión, crear un comando y ejecute el comando, los parámetros de enlace según sea necesario.  
  
 La primera forma de **abiertos** toma una cadena de comando de Unicode y no tiene ningún valor predeterminado.  
  
 La segunda forma de **abiertos** toma una cadena de comando de ANSI y ningún valor predeterminado (que se proporciona para ofrecer compatibilidad con las aplicaciones existentes de ANSI).  
  
 La tercera forma de **abiertos** permite que la cadena de comando como NULL, debido a un tipo `int` con un valor predeterminado es NULL. Se proporciona para llamar a `Open(session, NULL);` o `Open(session);` porque NULL es de tipo `int`. Esta versión requiere y valida que el `int` parámetro ser NULL.  
  
 Usar la forma del cuarta **abiertos** cuando ya ha creado un comando y desea realizar una sola [preparar](../../data/oledb/ccommand-prepare.md) y varias ejecuciones.  
  
> [!NOTE]
>  **Abra** llamadas **Execute**, que a su vez, llama `GetNextResult`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (Clase)](../../data/oledb/ccommand-class.md)
---
title: 'CCommand:: Create | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.Create
- CCommand::Create
dev_langs: C++
helpviewer_keywords: Create method [C++]
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f4bbd236c2ec7ae6857ede1ac64f738ca8600774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccommandcreate"></a>CCommand::Create
Llamadas [CCommand:: CreateCommand](../../data/oledb/ccommand-createcommand.md) para crear un comando para la sesión especificada, a continuación, llama [ICommandText:: SetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) para especificar el texto del comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `session`  
 [in] Una sesión en el que se va a crear el comando.  
  
 `wszCommand`  
 [in] Un puntero al texto Unicode de la cadena de comandos.  
  
 `szCommand`  
 [in] Un puntero al texto ANSI de la cadena de comandos.  
  
 `guidCommand`  
 [in] Un GUID que especifica la sintaxis y las reglas generales para el proveedor debe usar al analizar el texto del comando. Para obtener una descripción de dialectos, consulte [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) en el *referencia del programador de OLE DB*.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 La primera forma de **crear** toma una cadena de comando de Unicode. La segunda forma de **crear** toma una cadena de comando de ANSI (que se proporciona para ofrecer compatibilidad con las aplicaciones existentes de ANSI).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (Clase)](../../data/oledb/ccommand-class.md)
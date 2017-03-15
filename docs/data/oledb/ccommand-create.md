---
title: "CCommand::Create | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.Create"
  - "CCommand::Create"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Create (método) [C++]"
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CCommand::Create
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llama a [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) para crear un comando para la sesión especificada, llamar [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) para especificar el texto de comando.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `session`  
 \[in\] Una sesión en el que crear el comando.  
  
 `wszCommand`  
 \[in\] Un puntero al texto Unicode de la cadena de comando.  
  
 `szCommand`  
 \[in\] Un puntero al texto ANSI de la cadena de comando.  
  
 `guidCommand`  
 \[in\] GUID que especifica la sintaxis y las reglas generales para que el proveedor usa de analizar el texto de comando.  Para obtener una descripción de dialectos, vea [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 El primer formulario de **crear** toma una cadena de comando de Unicode.  El segundo formato de **crear** toma una cadena de comando ANSI \(proporcionada por compatibilidad con versiones anteriores las aplicaciones existentes de ANSI\).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CCommand \(Clase\)](../../data/oledb/ccommand-class.md)
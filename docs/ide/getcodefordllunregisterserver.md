---
title: "GetCodeForDllUnregisterServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForDllUnregisterServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllUnregisterServer (método)"
ms.assetid: 6b152943-8c30-49f4-a55c-d0cba8d27a17
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForDllUnregisterServer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el código apropiado para anular el registro de un servidor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      function GetCodeForDllUnregisterServer(   
   nLineStart,   
   nLineEnd    
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nLineStart`  
 El número de línea de base cero para el inicio de la función.  
  
 `nLineEnd`  
 El número de línea de base cero para el final de la función.  
  
## <a name="return-value"></a>Valor devuelto  
 Una cadena que contiene el código para anular el registro del servidor.  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para recuperar el código apropiado para anular el registro del servidor:  
  
|Número de línea|Código|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|_AtlModule.UpdateRegistryAppId(false);|  
|2|HRESULT hRes = _AtlModule.UnregisterServer(TRUE);|  
|3|Si (hRes! = S_OK)|  
|4|\treturn hRes;|  
|5|If (!) COleObjectFactory::UpdateRegistryAll(FALSE))|  
|6|\treturn ResultFromScode(SELFREG_E_CLASS);|  
|7|Devuelve S_OK;|  
  
 Para cada una de las líneas devueltas, `GetCodeForDllUnregisterServer` agrega una tabulación inicial (`\t`) y un par de caracteres "CR-LF" (retorno de carro - avance de línea) (`\r\n`).  
  
## <a name="example"></a>Ejemplo  
  
```  
// Get the lines numbered 2 and 3 above  
GetCodeForDllUnregisterServer(2, 3)  
  
// returns the following string  
// "\tHRESULT hRes = _AtlModule.UnregisterServer(TRUE);\r\n\tif (hRes != S_OK)\r\n"  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar los asistentes de C++ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para asistentes de C++](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear a un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetCodeForDllRegisterServer](../ide/getcodefordllregisterserver.md)
---
title: "GetCodeForDllRegisterServer | Microsoft Docs"
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
  - "GetCodeForDllRegisterServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllRegisterServer (método)"
ms.assetid: 2fe733ad-3f1e-4020-9ce3-68956da7d41d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetCodeForDllRegisterServer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el código apropiado para registrar un servidor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      function GetCodeForDllRegisterServer(   
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
 Una cadena que contiene el código para registrar el servidor  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para recuperar el código apropiado para registrar un servidor:  
  
|Número de línea|Código|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|_AtlModule.UpdateRegistryAppId(true);|  
|2|HRESULT hRes = _AtlModule.RegisterServer(TRUE);|  
|3|Si (hRes! = S_OK)|  
|4|\treturn hRes;|  
|5|If (!) COleObjectFactory::UpdateRegistryAll(TRUE))|  
|6|\treturn ResultFromScode(SELFREG_E_CLASS);|  
|7|Devuelve S_OK;|  
  
 Para cada una de las líneas devueltas, `GetCodeForDllRegisterServer` agrega una tabulación inicial (`\t`) y un par de caracteres "CR-LF" (retorno de carro - avance de línea) (`\r\n`).  
  
## <a name="example"></a>Ejemplo  
  
```  
// Get the lines numbered 2 and 3 above  
GetCodeForDllRegisterServer(2, 3)  
  
// returns the following string  
// "\tHRESULT hRes = _AtlModule.RegisterServer(TRUE);\r\n\tif (hRes != S_OK)\r\n"  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar los asistentes de C++ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para asistentes de C++](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear a un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetCodeForDllUnregisterServer](../ide/getcodefordllunregisterserver.md)
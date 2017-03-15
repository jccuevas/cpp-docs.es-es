---
title: "GetCodeForExitInstance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForExitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForExitInstance (método)"
ms.assetid: 41fe3d79-a1f4-4bb5-b3f5-7859e255b4e7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForExitInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el [ExitInstance](../Topic/CWinApp::ExitInstance.md) código para finalizar el asistente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      function GetCodeForExitInstance(   
   nLineStart,   
   nLineEnd    
)   
```  
  
#### <a name="parameters"></a>Parámetros  
 `nLineStart`  
 El número de línea de base cero para el inicio de la función.  
  
 `nLineEnd`  
 El número de línea de base cero para el final de la función.  
  
## <a name="return-value"></a>Valor devuelto  
 Una cadena que contiene el código para salir de la instancia del asistente.  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para recuperar el código apropiado para salir de una instancia del asistente:  
  
|Número de línea|Código ExitInstance|  
|-----------------|-----------------------|  
|0|_AtlModule.RevokeClassObjects();|  
|1|devolver CWinApp::ExitInstance();|  
  
 Para cada una de las líneas devueltas, `GetCodeForExitInstance` agrega una tabulación inicial (`\t`) y un par de caracteres "CR-LF" (retorno de carro - avance de línea) (`\r\n`).  
  
## <a name="example"></a>Ejemplo  
  
```  
if (!oExitInstance)  
   {  
      oExitInstance = oCWinApp.AddFunction("ExitInstance",   
      vsCMFunctionFunction, "BOOL", vsCMAddPositionEnd, vsCMAccessPublic,   
      strProjectCPP);  
      oExitInstance.BodyText = GetCodeForExitInstance(0, 1);  
   }  
// returns the following string  
// "\t_AtlModule.RevokeClassObjects();\r\n  
// \treturn CWinApp::ExitInstance();\r\n"  
else  
   {  
   oExitInstance.StartPointOf(vsCMPartBody,   
   vsCMWhereDefinition).CreateEditPoint().Insert(GetCodeForExitInstance(0,   
   0));  
// returns the following string  
// "\t_AtlModule.RevokeClassObjects();\r\n  
      oCM.Synchronize();  
   }  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar los asistentes de C++ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para asistentes de C++](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear a un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetCodeForDllCanUnloadNow](../ide/getcodefordllcanunloadnow.md)   
 [GetCodeForInitInstance](../ide/getcodeforinitinstance.md)
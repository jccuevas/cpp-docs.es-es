---
title: "GetCodeForDllCanUnloadNow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForDllCanUnloadNow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllCanUnloadNow (método)"
ms.assetid: 24ee3ef7-45be-4778-99e8-6df493f0782b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForDllCanUnloadNow
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el código apropiado para descargar la DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      function GetCodeForDllCanUnloadNow(   
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
 Una cadena que contiene el código para descargar la DLL.  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para recuperar el código apropiado para descargar la DLL. Llamar a esta función, crea una cadena única concatenando los elementos de matriz que se especifique.  
  
 La siguiente tabla muestra el código para descargar el archivo DLL.  
  
|Número de línea|Código|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|Si (_AtlModule.GetLockCount() > 0)|  
|2|\treturn S_FALSE;|  
|3|Devuelve S_OK;|  
  
 Para cada una de las líneas devueltas, `GetCodeForDllCanUnloadNow` agrega una tabulación inicial (`\t`) y un par de caracteres "CR-LF" (retorno de carro - avance de línea) (`\r\n`).  
  
## <a name="example"></a>Ejemplo  
  
```  
// Get the lines numbered 1 and 2 above  
GetCodeForDllCanUnloadNow(1, 2)  
  
// returns the following string  
// "\tif (_AtlModule.GetLockCount() > 0)\r\n\t\treturn S_FALSE;\r\n"  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar los asistentes de C++ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para asistentes de C++](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear a un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [GetCodeForDllGetClassObject](../ide/getcodefordllgetclassobject.md)   
 [GetCodeForExitInstance](../ide/getcodeforexitinstance.md)
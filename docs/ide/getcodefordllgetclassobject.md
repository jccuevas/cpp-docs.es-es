---
title: "GetCodeForDllGetClassObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForDllGetClassObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllGetClassObject (método)"
ms.assetid: 67b61b3b-9784-494f-ba01-17bffa9941ff
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForDllGetClassObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera el código para el objeto de clase DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      function GetCodeForDllGetClassObject(   
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
 Una cadena que contiene el código para obtener el objeto de clase.  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para recuperar el código para el objeto de clase. Llamar a esta función, crea una cadena única concatenando los elementos de matriz que se especifique.  
  
 La siguiente tabla muestra el código para obtener el código para el objeto de clase:  
  
|Número de línea|Código|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|Si (S_OK == _AtlModule.GetClassObject (rclsid, riid, ppv))|  
|2|\treturn S_OK;|  
|3|devolver AfxDllGetClassObject (rclsid, riid, ppv);|  
  
 Para cada una de las líneas devueltas, `GetCodeForDllGetClassObject` agrega una tabulación inicial (`\t`) y un par de caracteres "CR-LF" (retorno de carro - avance de línea) (`\r\n`).  
  
## <a name="example"></a>Ejemplo  
  
```  
// Get the lines numbered 1 and 2 above  
GetCodeForDllGetClassObject(1, 2)  
  
// returns the following string  
// "\tif (S_OK == _AtlModule.GetClassObject(rclsid, riid, ppv))\r\n\t\treturn S_OK;\r\n"  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar los asistentes de C++ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para asistentes de C++](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear a un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)
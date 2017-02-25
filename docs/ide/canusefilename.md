---
title: "CanUseFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CanUseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanUseFileName (método)"
ms.assetid: 60b669fa-9484-4435-b502-78ec8e960a00
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CanUseFileName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si existe un archivo.  Si el archivo existe y no está restringido, el asistente le pedirá al usuario que combine el código que va a agregarse al archivo.  
  
## Sintaxis  
  
```  
  
      function CanUseFileName(   
   strFileName,   
   bCheckIfMidlHeader,   
   bCannotExist,   
   bSetMergeFlag    
);  
```  
  
#### Parámetros  
 `strFileName`  
 Nombre del archivo que se va a comprobar.  
  
 *bCheckIfMidlHeader*  
 Se le asigna el valor **true** para comprobar si el nombre de archivo lo genera MIDL.  
  
 *bCannotExist*  
 Se le asigna el valor **true** para comprobar si el nombre de archivo existe y no puede sobrescribirse.  
  
 *bSetMergeFlag*  
 Se le asigna el valor **true** para incluir el símbolo MERG\_FILE, que indica que el usuario puede combinar el código en el nombre de archivo existente.  
  
## Valor devuelto  
 **true** si `strFileName` es único o si se puede anexar el código al archivo existente; de lo contrario, **false**.  
  
## Comentarios  
 Se llama a esta función para comprobar si existe un nombre de archivo determinado.  Si existe, y no lo ha creado MIDL o está restringido de alguna otra forma, la función le pedirá al usuario que combine el nuevo código en el archivo existente.  
  
 Si no existe y no está restringido, se creará un archivo con el nombre especificado.  
  
 Si el nombre de archivo lo ha creado MIDL o está restringido de alguna otra forma, el asistente mostrará un mensaje de error.  
  
## Ejemplo  
  
```  
case "HTML_FILE":  
if (!HTML_FILE.disabled)  
   {  
   if (!window.external.FindSymbol("HTML_FILE_VALID"))  
      {  
      bValid = CanUseFileName(obj.value, false, true);  
      if (!bValid)  
      break;  
      window.external.AddSymbol("HTML_FILE_VALID", true)  
      }  
   }  
   bValid = window.external.ValidateFile(HTML_FILE.value, vsCMValidateFileExtHtml);  
   break;   
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)
---
title: "Invoking Scripts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StringRegister"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scripts, invoking registry in ATL"
  - "StringRegister method"
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Invoking Scripts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[Usar parámetros reemplazables \(el preprocesador de registro\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) describe mapas de reemplazo y indica el método **AddReplacement**del registro.  El registro tiene ocho otros métodos específicos del script, y todos se describen en la tabla siguiente.  
  
|Método|sintaxis\/descripción|  
|------------|---------------------------|  
|**ResourceRegister**|*resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType`\);de**HRESULT ResourceRegister \(LPCOLESTR**<br /><br /> registra el script contenido en el recurso de un módulo.  *el resFileName* indica la ruta UNC al módulo propio.  `nID` y `szType` contienen el identificador y el tipo de recurso, respectivamente.|  
|**ResourceUnregister**|*resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType`\);de**HRESULT ResourceUnregister \(LPCOLESTR**<br /><br /> Anula el script contenido en el recurso de un módulo.  *el resFileName* indica la ruta UNC al módulo propio.  `nID` y `szType` contienen el identificador y el tipo de recurso, respectivamente.|  
|**ResourceRegisterSz**|*SzID* **, LPCOLESTR**  `szType`\);de**, LPCOLESTR** *de resFileName*de**HRESULT ResourceRegisterSz \(LPCOLESTR**<br /><br /> registra el script contenido en el recurso de un módulo.  *el resFileName* indica la ruta UNC al módulo propio.  *el szID* y `szType` contienen el identificador de cadena y el tipo de recurso, respectivamente.|  
|**ResourceUnregisterSz**|*SzID* **, LPCOLESTR**  `szType`\);de**, LPCOLESTR** *de resFileName*de**HRESULT ResourceUnregisterSz \(LPCOLESTR**<br /><br /> Anula el script contenido en el recurso de un módulo.  *el resFileName* indica la ruta UNC al módulo propio.  *el szID* y `szType` contienen el identificador de cadena y el tipo de recurso, respectivamente.|  
|**FileRegister**|*nombre de archivo* \);de**HRESULT FileRegister \(LPCOLESTR**<br /><br /> registra el script en un archivo.  *el nombre de archivo* es una ruta UNC a un archivo que contiene \(o\) es un script de recursos.|  
|**FileUnregister**|*nombre de archivo* \);de**HRESULT FileUnregister \(LPCOLESTR**<br /><br /> Anula el script en un archivo.  *el nombre de archivo* es una ruta UNC a un archivo que contiene \(o\) es un script de recursos.|  
|**StringRegister**|*datos* \);de**HRESULT StringRegister \(LPCOLESTR**<br /><br /> registra el script en una cadena.  *los datos* contiene script propio.|  
|**StringUnregister**|*datos* \);de**HRESULT StringUnregister \(LPCOLESTR**<br /><br /> Anula el script en una cadena.  *los datos* contiene script propio.|  
  
 **ResourceRegisterSz** y **ResourceUnregisterSz**, son similares a **ResourceRegister** y a **ResourceUnregister**, pero permiten especificar un identificador de cadena.  
  
 Los métodos **FileRegister** y **FileUnregister** son útiles si no desea que el script en un recurso o si desea que el script en su propio archivo.  Los métodos **StringRegister** y **StringUnregister** permiten que el archivo .rgs se almacenen en una cadena asignada dinámicamente.  
  
## Vea también  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
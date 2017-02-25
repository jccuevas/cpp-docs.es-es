---
title: "Registry Scripting Examples | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "registrar scripts [ATL]"
  - "Registro, Registrar"
  - "scripting, ejemplos"
  - "scripts, Registrar scripts"
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Registry Scripting Examples
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los ejemplos de script en este tema se muestra cómo agregar una clave en el registro del sistema, registran el servidor COM de registro, y especifican los árboles de análisis sintácticos.  
  
## Agregue una clave en HKEY\_CURRENT\_USER\-  
 El árbol de análisis siguiente se muestra un script simple que agregue una clave en el registro del sistema.  En particular, el script se agrega la clave, `MyVeryOwnKey`, a `HKEY_CURRENT_USER`.  También asigna el valor de cadena predeterminado de `HowGoesIt?` a la nueva clave:  
  
```  
HKEY_CURRENT_USER  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
```  
  
 Este script se puede fácilmente extender para definir subclaves varias como sigue:  
  
```  
HKCU  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
   {  
      'HasASubkey'  
      {  
         'PrettyCool?' = d '55'  
         val 'ANameValue' = s 'WithANamedValue'  
      }  
   }  
}  
```  
  
 ahora, el script agrega una subclave, `HasASubkey`, a `MyVeryOwnKey`.  a esta subclave, agrega la subclave de `PrettyCool?` \(con un valor predeterminado de `DWORD` de 55\) y `ANameValue` denominado valor \(con un valor de cadena de `WithANamedValue`\).  
  
##  <a name="_atl_register_the_registrar_com_server"></a> Registre el servidor COM de registro  
 El script siguiente registra el servidor COM propio del registro.  
  
```  
HKCR  
{  
   ATL.Registrar = s 'ATL Registrar Class'  
   {  
      CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
   }  
   NoRemove CLSID  
   {  
      ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} =  
                   s 'ATL Registrar Class'  
      {  
         ProgID = s 'ATL.Registrar'  
         InprocServer32 = s '%MODULE%'  
         {  
            val ThreadingModel = s 'Apartment'  
         }  
      }  
   }  
}  
```  
  
 En tiempo de ejecución, este árbol de análisis agrega la clave de `ATL.Registrar` a `HKEY_CLASSES_ROOT`.  En esta nueva clave, a continuación:  
  
-   Especifica `ATL Registrar Class` como valor de cadena predeterminado de la clave.  
  
-   agrega `CLSID` como subclave.  
  
-   especifica `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` para `CLSID`.  \(Este valor es el CLSID del registro para el uso con `CoCreateInstance`.\)  
  
 Puesto que se comparte `CLSID` , no debe quitar en el modo de Registro.  La instrucción, `NoRemove CLSID`, ello indica que `CLSID` debe estar abierto en modo del registro y omitir en el modo de Registro.  
  
 La instrucción de `ForceRemove` proporciona una función de mantenimiento quitando una clave y todas sus subclaves antes de volver a crear la clave.  esto puede ser útil si los nombres de las subclaves han cambiado.  En este ejemplo de script, comprobaciones de `ForceRemove` para ver si existe `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` ya.  Si lo hace, `ForceRemove`:  
  
-   Elimina de forma recursiva `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` y todas sus subclaves.  
  
-   reconstruye `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
-   Agrega `ATL Registrar Class` como valor de cadena predeterminado para `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
 El árbol de análisis ahora agrega dos nuevas subclaves a `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  La primera clave, `ProgID`, obtiene un valor de cadena predeterminado que sea ProgID.  La segunda clave, `InprocServer32`, obtiene un valor de cadena, `%MODULE%`, que es un valor de preprocesador explicado en la sección, [Usar parámetros reemplazables \(el preprocesador de registro\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), de este artículo.  `InprocServer32` también obtienen un valor denominado, `ThreadingModel`, con un valor de cadena de `Apartment`.  
  
## Especifique los árboles de análisis sintácticos varias  
 Para especificar más de un árbol de análisis en un script, coloque simplemente un árbol al final de otro.  Por ejemplo, el siguiente script agrega la clave, `MyVeryOwnKey`, los árboles de análisis sintácticos para `HKEY_CLASSES_ROOT` y `HKEY_CURRENT_USER`:  
  
```  
HKCR  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
HKEY_CURRENT_USER  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
```  
  
> [!NOTE]
>  En un script de registro, 4K es el tamaño máximo de token.  \(El símbolo consiste en cualquier elemento reconocible en la sintaxis.\) En el ejemplo anterior de script, `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, y `'HowGoesIt?'` son todos los tokens.  
  
## Vea también  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
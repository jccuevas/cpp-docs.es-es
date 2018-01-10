---
title: Ejemplos de secuencias de comandos de registro | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b2a5dfd3bd31674917a5b41174277ef787aff25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="registry-scripting-examples"></a>Ejemplos de secuencias de comandos del registro
Los ejemplos de secuencias de comandos en este tema muestran cómo agregar una clave al registro del sistema, registrar el registrador del servidor COM y especificar varios árboles de análisis.  
  
## <a name="add-a-key-to-hkeycurrentuser"></a>Agregar una clave a HKEY_CURRENT_USER  
 El siguiente árbol de análisis muestra una secuencia de comandos simple que agrega una clave única para el registro del sistema. En concreto, la secuencia de comandos agrega la clave, `MyVeryOwnKey`a `HKEY_CURRENT_USER`. También asigna el valor de cadena predeterminado de `HowGoesIt` a la nueva clave:  
  
```  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
 Este script se puede extender con facilidad para definir varias subclaves del siguiente modo:  
  
```  
HKCU  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
 {  
 'HasASubkey'  
 {  
 'PrettyCool' = d '55'  
    val 'ANameValue' = s 'WithANamedValue'  
 }  
 }  
}  
```  
  
 Ahora, la secuencia de comandos agrega una subclave, `HasASubkey`a `MyVeryOwnKey`. Para esta subclave, agrega tanto el `PrettyCool` subclave (su valor predeterminado es `DWORD` valo 55) y el `ANameValue` denominado valor (con un valor de cadena de `WithANamedValue`).  
  
##  <a name="_atl_register_the_registrar_com_server"></a>Registrar el registrador del servidor COM  
 La secuencia de comandos siguiente registra el propio servidor COM de registrador.  
  
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
  
 En tiempo de ejecución, este árbol de análisis agrega la `ATL.Registrar` clave a `HKEY_CLASSES_ROOT`. En esta nueva clave, a continuación, TI:  
  
-   Especifica `ATL Registrar Class` como valor de cadena del valor predeterminado de la clave.  
  
-   Agrega `CLSID` como una subclave.  
  
-   Especifica `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` para `CLSID`. (Este valor es el registrador CLSID para su uso con `CoCreateInstance`.)  
  
 Puesto que `CLSID` es compartido, no debe eliminarse en el modo de anular el registro. La instrucción `NoRemove CLSID`, para ello, lo que indica que `CLSID` debe abrirse en modo de registro y pasa por alto en modo de anular el registro.  
  
 El `ForceRemove` instrucción ofrece una función de mantenimiento mediante la eliminación de una clave y todas sus subclaves antes de volver a crear la clave. Esto puede resultar útil si han cambiado los nombres de las subclaves. En este ejemplo de scripting, `ForceRemove` comprueba si `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` ya existe. Si es así, `ForceRemove`:  
  
-   Elimina de forma recursiva `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` y todas sus subclaves.  
  
-   Vuelve a crear `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
-   Agrega `ATL Registrar Class` como el valor de cadena predeterminado de `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.  
  
 Ahora, el árbol de análisis agrega dos nuevas subclaves para `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. La primera clave, `ProgID`, obtiene un valor de cadena predeterminado que es el ProgID. La segunda clave, `InprocServer32`, obtiene un valor de cadena predeterminado, `%MODULE%`, que es un valor de preprocesador explicado en la sección [utilizar parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), de este artículo. `InprocServer32`También obtiene un valor con nombre, `ThreadingModel`, con un valor de cadena de `Apartment`.  
  
## <a name="specify-multiple-parse-trees"></a>Especificar varios árboles de análisis  
 Para especificar más de un árbol de análisis en una secuencia de comandos, basta con colocar un árbol al final de la otra. Por ejemplo, el siguiente script agrega la clave, `MyVeryOwnKey`, los árboles de análisis para ambos `HKEY_CLASSES_ROOT` y `HKEY_CURRENT_USER`:  
  
```  
HKCR  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
> [!NOTE]
>  En una secuencia de comandos del registrador, 4K es el tamaño máximo del token. (Un token es cualquier elemento reconocible en la sintaxis). En el ejemplo de secuencia de comandos anterior, `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, y `'HowGoesIt'` todos los símbolos (tokens).  
  
## <a name="see-also"></a>Vea también  
 [Crear scripts del registrador](../atl/creating-registrar-scripts.md)


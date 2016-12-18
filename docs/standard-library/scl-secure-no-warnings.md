---
title: "_SCL_SECURE_NO_WARNINGS | Microsoft Docs"
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
  - "_SCL_SECURE_NO_DEPRECATE"
  - "_SCL_SECURE_NO_WARNINGS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_SCL_SECURE_NO_DEPRECATE"
  - "_SCL_SECURE_NO_WARNINGS"
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _SCL_SECURE_NO_WARNINGS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Llamar a los métodos potencialmente no seguros en la biblioteca estándar de C\+\+ dará lugar a [Advertencia del compilador \(nivel 3\) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).  Para deshabilitar esta advertencia, defina **\_SCL\_SECURE\_NO\_WARNINGS** macro en el código:  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## Comentarios  
 Otras maneras de deshabilitar la inclusión de la advertencia C4996:  
  
-   Mediante la opción del compilador [\/D \(Definiciones de preprocesador\)](../build/reference/d-preprocessor-definitions.md) :  
  
    ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
    ```  
  
-   Mediante la opción del compilador [\/w](../build/reference/compiler-option-warning-level.md) :  
  
    ```  
    cl /wd4996 [other compiler options] myfile.cpp  
    ```  
  
-   Usar la directiva de [\#pragma warning](../preprocessor/warning.md) :  
  
    ```  
    #pragma warning(disable:4996)  
    ```  
  
 Asimismo, puede cambiar manualmente el nivel de la advertencia C4996 con la opción del compilador **\/w\<l\>\<n\>** .  Por ejemplo, establecer la advertencia C4996 al nivel 4:  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 Para obtener más información, vea [\/w, \/Wn, \/WX, \/Wall, \/wln, \/wdn, \/wen, \/won \(Nivel de advertencia\)](../build/reference/compiler-option-warning-level.md).  
  
## Vea también  
 [Bibliotecas seguras: Biblioteca estándar de C\+\+](../standard-library/safe-libraries-cpp-standard-library.md)
---
title: "Convertir proyectos de modo mixto a lenguaje intermedio puro | Microsoft Docs"
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
  - "lenguaje intermedio, aplicaciones en modo mixto"
  - "aplicaciones en modo mixto"
  - "aplicaciones en modo mixto, lenguaje intermedio"
  - "proyectos [C++], convertir a lenguaje intermedio"
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Convertir proyectos de modo mixto a lenguaje intermedio puro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, todos los proyectos CLR de Visual C\+\+ se vinculan a las bibliotecas en tiempo de ejecución de C.  Por eso, estos proyectos se clasifican como aplicaciones de modo mixto, ya que combinan código nativo con código orientado a Common Language Runtime \(código administrado\).  Cuando se compilan, la compilación se lleva a cabo en lenguaje intermedio \(IL\), también conocido como lenguaje intermedio de Microsoft \(MSIL\).  
  
### Para convertir la aplicación de modo mixto en lenguaje intermedio puro  
  
1.  Quite los vínculos a las [Bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md) \(CRT\):  
  
    1.  En el archivo .cpp que define el punto de entrada de la aplicación, cambie el punto de entrada a `Main()`.  El uso de `Main()` indica que el proyecto no se vincula al CRT.  
  
    2.  En el Explorador de soluciones, haga clic con el botón secundario del mouse en el proyecto y seleccione **Propiedades** en el menú contextual para abrir las páginas de propiedades de la aplicación.  
  
    3.  En la página de propiedades del proyecto **Avanzadas** para el campo **Vinculador**, seleccione **Punto de entrada** y escriba **Main** en este campo.  
  
    4.  Para aplicaciones de consola, seleccione el campo **Subsistema** en la página de propiedades de proyecto **Sistema** para el **Vinculador** y cámbielo a **Consola \(\/SUBSYSTEM:CONSOLE\)**.  
  
        > [!NOTE]
        >  No es necesario que establezca esta propiedad para aplicaciones de formularios Windows Forms porque el campo **Subsistema** está establecido de forma predeterminada en **Windows \(\/SUBSYSTEM:WINDOWS\)**.  
  
    5.  En stdafx.h, marque como comentario todas las instrucciones `#include`.  Por ejemplo, en las aplicaciones de consola:  
  
        ```  
        // #include <iostream>  
        // #include <tchar.h>  
        ```  
  
         O bien  
  
         Por ejemplo, en las aplicaciones de formularios Windows Forms:  
  
        ```  
        // #include <stdlib.h>  
        // #include <malloc.h>  
        // #include <memory.h>  
        // #include <tchar.h>  
        ```  
  
    6.  Para las aplicaciones de Windows Forms, en Form1.cpp, marque como comentario la instrucción `#include` que hace referencia a windows.h.  Por ejemplo:  
  
        ```  
        // #include <windows.h>  
        ```  
  
2.  Agregue el código siguiente a stdafx.h:  
  
    ```  
    #ifndef __FLTUSED__  
    #define __FLTUSED__  
       extern "C" __declspec(selectany) int _fltused=1;  
    #endif  
    ```  
  
3.  Quite todos los tipos no administrados:  
  
    1.  Donde sea necesario, reemplace los tipos no administrados por referencias a estructuras desde el espacio de nombres [System](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx).  Los tipos administrados más comunes se enumeran en la tabla que sigue a continuación:  
  
        |Estructura|Descripción|  
        |----------------|-----------------|  
        |[\<caps:sentence id\="tgt24" sentenceid\="84e2c64f38f78ba3ea5c905ab5a2da27" class\="tgtSentence"\>Boolean\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.boolean\(v=vs.140\).aspx)|Representa un valor booleano.|  
        |[\<caps:sentence id\="tgt26" sentenceid\="40ea57d3ee3c07bf1c102b466e1c3091" class\="tgtSentence"\>Byte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.byte\(v=vs.140\).aspx)|Representa un entero de 8 bits sin signo.|  
        |[\<caps:sentence id\="tgt28" sentenceid\="a87deb01c5f539e6bda34829c8ef2368" class\="tgtSentence"\>Char\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char\(v=vs.140\).aspx)|Representa un carácter Unicode.|  
        |[\<caps:sentence id\="tgt30" sentenceid\="dfeaaeb4316477bd556ea5e8c3295887" class\="tgtSentence"\>DateTime\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.datetime.datetime.aspx)|Representa un instante de tiempo, normalmente expresado en forma de fecha y hora del día.|  
        |[\<caps:sentence id\="tgt32" sentenceid\="bdaa3c20a3e3851599514f7c6be5f62f" class\="tgtSentence"\>Decimal\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.decimal\(v=vs.140\).aspx)|Representa un número decimal.|  
        |[\<caps:sentence id\="tgt34" sentenceid\="e8cd7da078a86726031ad64f35f5a6c0" class\="tgtSentence"\>Double\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double\(v=vs.140\).aspx)|Representa un número de punto flotante de precisión doble.|  
        |[\<caps:sentence id\="tgt36" sentenceid\="1e0ca5b1252f1f6b1e0ac91be7e7219e" class\="tgtSentence"\>Guid\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.guid\(v=vs.140\).aspx)|Representa un identificador exclusivo global \(GUID\).|  
        |[\<caps:sentence id\="tgt38" sentenceid\="ce80d5ec65b1d2a2f1049eadc100db23" class\="tgtSentence"\>Int16\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int16\(v=vs.140\).aspx)|Representa un entero de 16 bits con signo.|  
        |[\<caps:sentence id\="tgt40" sentenceid\="0241adbbd83925f051b694d40f02747f" class\="tgtSentence"\>Int32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int32\(v=vs.140\).aspx)|Representa un entero de 32 bits con signo.|  
        |[\<caps:sentence id\="tgt42" sentenceid\="ff9b3f96d37353c528517bc3656a00a8" class\="tgtSentence"\>Int64\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int64\(v=vs.140\).aspx)|Representa un entero de 64 bits con signo.|  
        |[\<caps:sentence id\="tgt44" sentenceid\="7f1db863563907cf33604ed7fad6b111" class\="tgtSentence"\>IntPtr\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.intptr\(v=vs.140\).aspx)|Tipo específico de plataforma que se utiliza para representar un puntero o un identificador.|  
        |[\<caps:sentence id\="tgt46" sentenceid\="943756eb7841efcc43b7cd37d7254c76" class\="tgtSentence"\>SByte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.byte.aspx)|Representa un entero con signo de 8 bits.|  
        |[\<caps:sentence id\="tgt48" sentenceid\="dd5c07036f2975ff4bce568b6511d3bc" class\="tgtSentence"\>Single\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.single.aspx)|Representa un número de punto flotante de precisión sencilla.|  
        |[\<caps:sentence id\="tgt50" sentenceid\="90150402997ea9c8dc45cc4d41bb28cb" class\="tgtSentence"\>Timespan\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.timespan\(v=vs.140\).aspx)|Representa un intervalo de tiempo.|  
        |[\<caps:sentence id\="tgt52" sentenceid\="a00ef2ef85ff67b7b39339886f19044f" class\="tgtSentence"\>UInt16\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint16\(v=vs.140\).aspx)|Representa un entero de 16 bits sin signo.|  
        |[\<caps:sentence id\="tgt54" sentenceid\="3de84ad0700f2a1571f633d399e1900e" class\="tgtSentence"\>UInt32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint32\(v=vs.140\).aspx)|Representa un entero de 32 bits sin signo.|  
        |[\<caps:sentence id\="tgt56" sentenceid\="2e8d31865e5d4b9d8611e1b991baed07" class\="tgtSentence"\>UInt64\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint64\(v=vs.140\).aspx)|Representa un entero de 64 bits sin signo.|  
        |[\<caps:sentence id\="tgt58" sentenceid\="92d74abda31865424016b16e2c806a66" class\="tgtSentence"\>UIntPtr\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uintptr\(v=vs.140\).aspx)|Tipo específico de plataforma que se utiliza para representar un puntero o un identificador.|  
        |[\<caps:sentence id\="tgt60" sentenceid\="cab8111fd0b710a336c898e539090e34" class\="tgtSentence"\>Tipo Void\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.void\(v=vs.140\).aspx)|Indica un método que devuelve un valor, es decir, el método tiene el tipo de valor devuelto void.|
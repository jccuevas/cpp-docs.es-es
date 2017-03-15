---
title: "Inicializar archivos DLL que no est&#225;n basados en MFC | Microsoft Docs"
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
  - "DLL [C++], no basada en MFC"
  - "inicializar DLL"
  - "DLL no basada en MFC [C++]"
ms.assetid: 2622b32a-28f9-4d61-9e46-6c19aaf8b7ad
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Inicializar archivos DLL que no est&#225;n basados en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para inicializar archivos DLL que no están basados en MFC, el código fuente del archivo DLL debe contener una función denominada `DllMain`.  El código siguiente presenta una estructura básica que muestra la posible apariencia de la definición de `DllMain`:  
  
```  
BOOL APIENTRY DllMain(HANDLE hModule,   
                      DWORD  ul_reason_for_call,   
                      LPVOID lpReserved)  
{  
    switch( ul_reason_for_call ) {  
    case DLL_PROCESS_ATTACH:  
    ...  
    case DLL_THREAD_ATTACH:  
    ...  
    case DLL_THREAD_DETACH:  
    ...  
    case DLL_PROCESS_DETACH:  
    ...  
    }  
    return TRUE;  
}  
```  
  
> [!NOTE]
>  En la documentación de [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] para **DllEntryPoint**, se indica que el nombre real de la función de punto de entrada debe especificarse en la línea de comandos del vinculador con la opción \/ENTRY.  En Visual C\+\+ no necesita utilizar la opción \/ENTRY si el nombre de la función de punto de entrada es `DllMain`.  De hecho, si utiliza la opción \/ENTRY y asigna a la función de punto de entrada un nombre distinto de `DllMain`, la biblioteca en tiempo de ejecución de C no se inicializará correctamente.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [\<caps:sentence id\="tgt7" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>Especificación de funciones para DllMain \(SDK de Windows\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt8" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>Función de punto de entrada de biblioteca de vínculos dinámicos \(SDK de Windows\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
-   [Comportamiento de la biblioteca en tiempo de ejecución de C y \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
## Vea también  
 [Inicializar un archivo DLL](../build/initializing-a-dll.md)
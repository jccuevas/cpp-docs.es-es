---
title: "/SAFESEH (La imagen tiene controladores de excepciones seguros) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/SAFESEH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SAFESEH (opción del vinculador)"
  - "-SAFESEH (opción del vinculador)"
  - "SAFESEH (opción del vinculador)"
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /SAFESEH (La imagen tiene controladores de excepciones seguros)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SAFESEH[:NO]  
```  
  
 Cuando se especifica **\/SAFESEH**, el vinculador solo generará una imagen si también puede generar una tabla de los controladores de excepciones seguros de la imagen.  Esta tabla especifica al sistema operativo qué controladores de excepciones son válidos para la imagen.  
  
 **\/SAFESEH** solo es válido al vincular para destinos x86.  **\/SAFESEH** no se admite en plataformas en las que ya se han tenido en cuenta los controladores de excepciones.  Por ejemplo, en [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] y ARM, todos los controladores de excepciones se tienen en cuenta en PDATA.  ML64.exe tiene compatibilidad para agregar anotaciones que emiten información de SEH \(XDATA y PDATA\) en la imagen, lo que permite desenredar a través de las funciones de ml64.  Para obtener más información, vea [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
 Cuando no se especifica **\/SAFESEH**, el vinculador producirá una imagen con una tabla de controladores de excepciones seguros si todos los módulos son compatibles con la característica de control de excepciones seguro.  Si algún módulo no fuera compatible con la característica de control de excepciones seguro, la imagen resultante no contendría una tabla de controladores de excepciones seguros.  Si [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) especifica WINDOWSCE o alguna de las opciones EFI\_\*, el vinculador no intentará generar una imagen con una tabla de controladores de excepciones seguros, ya que ninguno de esos subsistemas puede utilizar la información.  
  
 Si no se especifica **\/SAFESEH:NO**, el vinculador no producirá una imagen con una tabla de controladores de excepciones seguros aunque todos los módulos sean compatibles con la característica de control de excepciones seguro.  
  
 La razón más común para que el vinculador no pueda generar una imagen se debe a que uno o varios de los archivos de entrada \(módulos\) para el vinculador no es compatible con la característica del controlador de excepciones seguro.  Una razón habitual para que un módulo no sea compatible con los controladores de excepciones seguros se debe a que se creó con un compilador de una versión anterior de Visual C\+\+.  
  
 Una función también puede registrarse como controlador de excepciones estructurado mediante [.SAFESEH](../../assembler/masm/dot-safeseh.md).  
  
 No es posible marcar un binario existente para indicar que dispone de controladores de excepciones seguros \(o no dispone de controladores de excepciones\). La información sobre control de excepciones seguro se debe agregar en tiempo de compilación.  
  
 La capacidad del vinculador para compilar una tabla de controladores de excepciones seguros depende de que la aplicación utilice la biblioteca en tiempo de ejecución de C.  Si vincula con la opción [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) y desea obtener una tabla de controladores de excepciones seguros, deberá suministrar un struct de configuración de carga \(como el que se encuentra en el archivo de código fuente loadcfg.c de CRT\) que contenga todas las entradas definidas para Visual C\+\+.  Por ejemplo:  
  
```  
#include <windows.h>  
extern DWORD_PTR __security_cookie;  /* /GS security cookie */  
  
/*  
 * The following two names are automatically created by the linker for any  
 * image that has the safe exception table present.  
*/  
  
extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */  
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is  
                                           the count of table entries */  
typedef struct {  
    DWORD       Size;  
    DWORD       TimeDateStamp;  
    WORD        MajorVersion;  
    WORD        MinorVersion;  
    DWORD       GlobalFlagsClear;  
    DWORD       GlobalFlagsSet;  
    DWORD       CriticalSectionDefaultTimeout;  
    DWORD       DeCommitFreeBlockThreshold;  
    DWORD       DeCommitTotalFreeThreshold;  
    DWORD       LockPrefixTable;            // VA  
    DWORD       MaximumAllocationSize;  
    DWORD       VirtualMemoryThreshold;  
    DWORD       ProcessHeapFlags;  
    DWORD       ProcessAffinityMask;  
    WORD        CSDVersion;  
    WORD        Reserved1;  
    DWORD       EditList;                   // VA  
    DWORD_PTR   *SecurityCookie;  
    PVOID       *SEHandlerTable;  
    DWORD       SEHandlerCount;  
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;  
  
const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {  
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    &__security_cookie,  
    __safe_se_handler_table,  
    (DWORD)(DWORD_PTR) &__safe_se_handler_count  
};  
```  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)
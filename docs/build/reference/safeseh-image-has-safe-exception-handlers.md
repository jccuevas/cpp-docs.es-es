---
title: /SAFESEH (La imagen tiene controladores de excepciones seguros)
ms.date: 11/04/2016
f1_keywords:
- /SAFESEH
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
ms.openlocfilehash: 62784933cbecd4f312c52ae98cab7d232b893f35
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822345"
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (La imagen tiene controladores de excepciones seguros)

```
/SAFESEH[:NO]
```

Cuando **/SAFESEH** se especifica, el vinculador solo generará una imagen si también puede generar una tabla de controladores de excepciones seguros de la imagen. Esta tabla especifica al sistema operativo qué controladores de excepciones son válidos para la imagen.

**/ SAFESEH** solo es válido al vincular para x86 destinos. **/ SAFESEH** no se admite para las plataformas que ya tienen los controladores de excepción que se ha indicado. Por ejemplo, en x64 y ARM, todos los controladores de excepciones se tienen en cuenta en PDATA. ML64.exe tiene compatibilidad para agregar anotaciones que emiten información de SEH (XDATA y PDATA) en la imagen, lo que permite desenredar a través de las funciones de ml64. Consulte [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) para obtener más información.

Si **/SAFESEH** no se especifica, el vinculador producirá una imagen con una tabla de controladores de excepciones seguros si todos los módulos son compatibles con la característica de control de excepciones seguro. Si algún módulo no fuera compatible con la característica de control de excepciones seguro, la imagen resultante no contendría una tabla de controladores de excepciones seguros. Si [/Subsystem](subsystem-specify-subsystem.md) especifica WINDOWSCE o alguna de las opciones EFI_ *, el vinculador no intentará generar una imagen con una tabla de controladores de excepciones seguros, ya que ninguno de esos subsistemas puede utilizar la información.

Si **/SAFESEH: no** se especifica, el vinculador no producirá una imagen con una tabla de controladores de excepciones seguros aunque todos los módulos son compatibles con la característica de control de excepciones seguro.

La razón más común para que el vinculador no pueda generar una imagen se debe a que uno o varios de los archivos de entrada (módulos) para el vinculador no es compatible con la característica del controlador de excepciones seguro. Una razón habitual para que un módulo no sea compatible con los controladores de excepciones seguros se debe a que se creó con un compilador de una versión anterior de Visual C++.

También puede registrar una función como controlador de excepciones estructurado mediante [. SAFESEH](../../assembler/masm/dot-safeseh.md).

No es posible marcar un binario existente para indicar que dispone de controladores de excepciones seguros (o no dispone de controladores de excepciones). La información sobre control de excepciones seguro se debe agregar en tiempo de compilación.

La capacidad del vinculador para compilar una tabla de controladores de excepciones seguros depende de que la aplicación utilice la biblioteca en tiempo de ejecución de C. Si crea un vínculo con [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) y desea que una tabla de controladores de excepciones seguros, deberá suministrar un struct de configuración de carga (por ejemplo puede encontrarse en el archivo de código fuente loadcfg.c de CRT) que contiene todas las entradas definidas para Visual C++. Por ejemplo:

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

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)

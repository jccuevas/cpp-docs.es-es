---
title: "Ejemplo de programa de texto genérico | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- _TCHAR type
- mappings, TCHAR.H data types
- generic-text example [CRT]
- TCHAR type
- TCHAR.H data types, mapping
ms.assetid: a03de0db-8118-4bd9-a03f-640e8dfc5ed3
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 0cdc18215fe80c4165ffa03a5d789af0ebc95b40
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="a-sample-generic-text-program"></a>Ejemplo de programa de texto genérico
**Específicos de Microsoft**  
  
 El siguiente programa, GENTEXT.C, ofrece una ilustración más detallada del uso de las asignaciones de texto genérico definidas en TCHAR.H:  
  
```  
// GENTEXT.C  
// use of generic-text mappings defined in TCHAR.H  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <direct.h>  
#include <errno.h>  
#include <tchar.h>  
  
int __cdecl _tmain(int argc, _TCHAR **argv, _TCHAR **envp)  
{  
   _TCHAR buff[_MAX_PATH];  
   _TCHAR *str = _T("Astring");  
   char *amsg = "Reversed";  
   wchar_t *wmsg = L"Is";  
  
#ifdef _UNICODE  
   printf("Unicode version\n");  
#else /* _UNICODE */  
#ifdef _MBCS  
   printf("MBCS version\n");  
#else  
   printf("SBCS version\n");  
#endif  
#endif /* _UNICODE */  
  
   if (_tgetcwd(buff, _MAX_PATH) == NULL)  
       printf("Can't Get Current Directory - errno=%d\n", errno);  
   else  
       _tprintf(_T("Current Directory is '%s'\n"), buff);  
   _tprintf(_T("'%s' %hs %ls:\n"), str, amsg, wmsg);  
   _tprintf(_T("'%s'\n"), _tcsrev(_tcsdup(str)));  
   return 0;  
}  
  
```  
  
 Si se ha definido `_MBCS`, GENTEXT.C se asigna al programa MBCS siguiente:  
  
```  
// crt_mbcsgtxt.c  
  
/*   
 * Use of generic-text mappings defined in TCHAR.H  
 * Generic-Text-Mapping example program  
 * MBCS version of GENTEXT.C  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <mbstring.h>  
#include <direct.h>  
  
int __cdecl main(int argc, char **argv, char **envp)  
{  
   char buff[_MAX_PATH];  
   char *str = "Astring";  
   char *amsg = "Reversed";  
   wchar_t *wmsg = L"Is";  
  
   printf("MBCS version\n");  
  
   if (_getcwd(buff, _MAX_PATH) == NULL) {  
       printf("Can't Get Current Directory - errno=%d\n", errno);  
   }  
   else {  
       printf("Current Directory is '%s'\n", buff);  
   }  
  
   printf("'%s' %hs %ls:\n", str, amsg, wmsg);  
   printf("'%s'\n", _mbsrev(_mbsdup((unsigned char*) str)));  
   return 0;  
}  
```  
  
 Si se ha definido `_UNICODE`, GENTEXT.C se asigna a la siguiente versión Unicode del programa. Para obtener más información sobre el uso de `wmain` en programas Unicode como sustituto de `main`, consulte [Usar wmain](../c-language/using-wmain.md) en *Referencia del lenguaje C*.  
  
```  
// crt_unicgtxt.c  
  
/*   
 * Use of generic-text mappings defined in TCHAR.H  
 * Generic-Text-Mapping example program  
 * Unicode version of GENTEXT.C  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <direct.h>  
  
int __cdecl wmain(int argc, wchar_t **argv, wchar_t **envp)  
{  
   wchar_t buff[_MAX_PATH];  
   wchar_t *str = L"Astring";  
   char *amsg = "Reversed";  
   wchar_t *wmsg = L"Is";  
  
   printf("Unicode version\n");  
  
   if (_wgetcwd(buff, _MAX_PATH) == NULL) {  
      printf("Can't Get Current Directory - errno=%d\n", errno);  
   }  
   else {  
       wprintf(L"Current Directory is '%s'\n", buff);  
   }  
  
   wprintf(L"'%s' %hs %ls:\n", str, amsg, wmsg);  
   wprintf(L"'%s'\n", wcsrev(wcsdup(str)));  
   return 0;  
}  
```  
  
 Si no se han definido `_MBCS` ni `_UNICODE`, GENTEXT.C se asigna al código ASCII de byte único, como sigue:  
  
```  
// crt_sbcsgtxt.c  
/*   
 * Use of generic-text mappings defined in TCHAR.H  
 * Generic-Text-Mapping example program  
 * Single-byte (SBCS) Ascii version of GENTEXT.C  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <direct.h>  
  
int __cdecl main(int argc, char **argv, char **envp)  
{  
   char buff[_MAX_PATH];  
   char *str = "Astring";  
   char *amsg = "Reversed";  
   wchar_t *wmsg = L"Is";  
  
   printf("SBCS version\n");  
  
   if (_getcwd(buff, _MAX_PATH) == NULL) {  
       printf("Can't Get Current Directory - errno=%d\n", errno);  
   }  
   else {  
       printf("Current Directory is '%s'\n", buff);  
   }  
  
   printf("'%s' %hs %ls:\n", str, amsg, wmsg);  
   printf("'%s'\n", strrev(strdup(str)));  
   return 0;  
}  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md)   
 [Asignaciones de tipos de datos](../c-runtime-library/data-type-mappings.md)   
 [Asignaciones de constantes y de variables globales](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Asignaciones de rutinas](../c-runtime-library/routine-mappings.md)   
 [Usar asignaciones de texto genérico](../c-runtime-library/using-generic-text-mappings.md)

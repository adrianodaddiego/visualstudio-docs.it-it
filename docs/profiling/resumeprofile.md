---
title: ResumeProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e0d9db4660936629c1e9dd6a5b7ff9704a7e7e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814098"
---
# <a name="resumeprofile"></a>ResumeProfile
Il metodo `ResumeProfile` decrementa il contatore Suspend/Resume per il livello di profilatura specificato.

## <a name="syntax"></a>Sintassi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parametri
 `Level`

 Indica il livello di profilatura a cui può essere applicata la raccolta di dati sulle prestazioni. Gli enumeratori **PROFILE_CONTROL_LEVEL** seguenti possono essere usati per indicare uno dei tre livelli a cui può essere applicata la raccolta di dati sulle prestazioni:

|Enumerator|Description|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Impostazione del livello globale con effetti su tutti i processi e i thread nell'esecuzione della profilatura.|
|PROFILE_PROCESSLEVEL|Impostazione del livello processo con effetti su tutti i thread che fanno parte del processo specificato.|
|PROFILE_THREADLEVEL|Impostazione del livello thread con effetti sul thread specificato.|

 `dwId`

 Identificatore del processo o del thread generato dal sistema.

## <a name="property-valuereturn-value"></a>Valore proprietà/valore restituito
 La funzione indica esito l'esito positivo o negativo usando l'enumerazione **PROFILE_COMMAND_STATUS**. Il valore restituito può essere uno dei seguenti:

|Enumerator|Description|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|L'ID dell'elemento di profilatura non esiste.|
|PROFILE_ERROR_LEVEL_NOEXIST|Il livello di profilatura specificato non esiste.|
|PROFILE_ERROR_MODE_NEVER|La modalità di profilatura è stata impostata su NEVER al momento della chiamata della funzione.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|La chiamata della funzione di profilatura, il livello di profilatura o la combinazione di chiamata e livello non sono ancora stati implementati.|
|PROFILE_OK|La chiamata è stata completata correttamente.|

## <a name="remarks"></a>Osservazioni
 Il valore iniziale del contatore Suspend/Resume è 0. Ogni chiamata a SuspendProfile aggiunge 1 al conteggio di Suspend/Resume. Ogni chiamata a ResumeProfile sottrae 1.

 Quando il conteggio di Suspend/Resume è maggiore di 0, lo stato di Suspend/Resume per il livello è OFF. Quando il conteggio è minore o uguale a 0, lo stato di Suspend/Resume è ON.

 Se lo stato di Start/Stop e lo stato di Suspend/Resume sono entrambi ON, lo stato di profilatura per il livello è ON. Affinché un thread venga incluso nella profilatura, gli stati dei livelli globale, processo e thread per il thread devono essere tutti ON.

## <a name="net-framework-equivalent"></a>Equivalente .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informazioni sulla funzione
 Intestazione: Dichiarata in *VSPerf.h*

 Libreria di importazione: *VSPerf.lib*

## <a name="example"></a>Esempio
 L'esempio seguente illustra la funzione ResumeProfile. Nell'esempio si presuppone che sia stata effettuata una chiamata al metodo SuspendProfile per lo stesso thread o processo identificato da [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
void ExerciseResumeProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the Suspend/Resume
    // count; each call to ResumeProfile subtracts 1.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call to ResumeProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = ResumeProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("ResumeProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Vedere anche
- [Riferimenti per le API del profiler di Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)
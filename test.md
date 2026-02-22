# Tests

## Dostoyevsky Idiot

### Timeline 

```mermaid
timeline
    title Narrative Timeline of The Idiot
    Part I : The Arrival : Prince Myshkin arrives in St. Petersburg from Switzerland.
           : The Yepanchin Meeting : Myshkin meets the General, Lizaveta, and their daughters.
           : The Portrait : Myshkin sees Nastasya's portrait at Ganya's; the obsession begins.
           : The Birthday Party : Rogozhin arrives with 100,000 rubles. Nastasya throws the money in the fire and leaves with him.
    The Interlude : Six Months Gap : Myshkin, Rogozhin, and Nastasya move between Moscow and the provinces.
                  : The Dark Brotherhood : Myshkin and Rogozhin exchange crosses; Rogozhin later attempts to murder Myshkin.
    Part II & III : Pavlovsk Summer : The society moves to the countryside. 
                  : The Scandal at the Green Bench : Aglaya and Nastasya's rivalry intensifies through letters and public snubs.
                  : Ippolit’s 'Explanation' : Ippolit attempts public suicide after reading his nihilistic manifesto.
    Part IV : The Final Confrontation : Aglaya and Nastasya meet face-to-face. Myshkin hesitates, losing Aglaya.
            : The Failed Wedding : Nastasya flees the altar with Rogozhin at the last second.
            : The Murder : Rogozhin kills Nastasya. Myshkin finds him; they keep vigil over her body.
    Epilogue : The Aftermath : Rogozhin is sent to Siberia. Myshkin returns to a state of idiocy in Switzerland.
```


## Chart of Idiot's characters

```mermaid
graph TD
    %% Central Characters
    Myshkin((Prince Myshkin))
    Nastasya(Nastasya Filippovna)
    Rogozhin(Parfyon Rogozhin)
    
    %% Yepanchin Family
    subgraph Yepanchins [The Yepanchin Household]
        GeneralY[General Yepanchin]
        Lizaveta[Lizaveta Prokofyevna]
        Aglaya(Aglaya Ivanovna)
        Alexandra[Alexandra]
        Adelaida[Adelaida]
    end

    %% Ivolgin Family
    subgraph Ivolgins [The Ivolgin Household]
        GeneralI[General Ivolgin]
        Nina[Nina Alexandrovna]
        Ganya[Gavrila 'Ganya' Ivolgin]
        Varvara[Varvara Ivolgina]
        Ptitsyn[Ptitsyn]
    end

    %% Supporting Characters
    Ippolit[Ippolit Terentyev]
    Lebedev[Lukyan Lebedev]
    Totsky[Afanasy Totsky]

    %% Relationships
    Myshkin -- "Compassionate Love" --> Nastasya
    Myshkin -- "Spiritual Brothers" --- Rogozhin
    Myshkin -- "Idealistic Romance" --> Aglaya
    
    Rogozhin -- "Obsessive Passion" --> Nastasya
    Nastasya -- "Self-Destructive Flight" --> Rogozhin
    
    Totsky -- "Original Seducer" --> Nastasya
    Ganya -- "Wants to marry for money" --> Nastasya
    Ganya -- "Social Ambition" --> Aglaya
    
    Aglaya -- "Jealousy" --> Nastasya
    
    %% Family Ties
    Lizaveta --- Aglaya
    GeneralY --- Aglaya
    GeneralI --- Ganya
    Varvara --- Ganya
    Varvara --- Ptitsyn
    
    %% Philosophers/Schemers
    Myshkin --- Ippolit
    Myshkin --- Lebedev
```

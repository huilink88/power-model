# Lines
## Functions


# Batteries
## Functions
* resource adequacy
* peak capacity
* black-start or local weak-grid issues
* frequency control and ancillary services (FCAS)
* congestion relief
* circuit trips (avoid)


# Grid Management
## Circuit Trips (avoid)
To survive the loss of one line or a big generator, system operators must leave “headroom” on the interconnector, so it might cap imports at (say) X MW to avoid thermal overload if a circuit trips. Grid must be N-1 securem meaning if one circuit trips, the other must be able to safely carry whatever flow ends up on it.
> Imagine an interconnector that’s effectively two parallel circuits between Region A and Region B. Each circuit has a thermal rating of, say, 1,000 MW. Together, when both are in service, you might allow up to 2,000 MW of flow A → B. Suppose you’re sending 1,800 MW A → B over the two circuits:
> 
> Before trip:
> Circuit 1: 900 MW, Circuit 2: 900 MW
> 
> Now one circuit trips (say Circuit 2).
>
> Immediately after the trip, almost all of that 1,800 MW has to go through the remaining circuit (the power doesn’t vanish—loads in Region B still need it). So:
> Circuit 1 jumps close to 1,800 MW, which exceeds its 1,000 MW rating → thermal overload.
>
> To avoid this, system operator might cap the pre-fault flow at, say, 1,000 MW total across both circuits, so that:
>
> Pre-fault: 500 + 500
>
> Post-fault (one trips): remaining line ≈ 1,000 MW → at the rating, but not above.
>
> That’s the “headroom”: you could physically carry 2,000 MW with both lines healthy, but you choose to carry less so that if one line fails, the other isn’t overloaded.

**Management using batteries**
>For a line trip:
>
>  Without the battery:
>
>      One circuit trips → remaining circuit suddenly must carry almost the full pre-fault flow → risk of overload.
>
>  With the battery:
>
>    As soon as a line trips, the battery injects power on the B side, effectively reducing what needs to come across the remaining line.
>    Post-fault flow on the surviving circuit is lower, safely within rating.
>    That means system operator can allow higher pre-fault interconnector flow (less headroom) because the battery will “catch” the contingency.
>
>For a generator trip in the importing region:
>
>  Without the battery:
>
>    Generator in B trips → imports on the interconnector jump up to cover the deficit.
>
>  With the battery:
>
>    Generator in B trips → battery instantly discharges, supplying some or all of the missing 500 MW locally.
>    The interconnector doesn’t have to ramp as hard, so its post-fault flow stays within limits.
>    Again, this lets AEMO run the interconnector at a higher pre-fault flow, knowing the battery will limit the post-fault increase.

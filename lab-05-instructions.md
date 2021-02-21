Instructions for Lab \#5
================
Jonathan Gilligan
Lab: Feb. 22; Due: Mar. 1

-   [Exercises with clouds and
    feedbacks](#exercises-with-clouds-and-feedbacks)
-   [Exercises](#exercises)
    -   [General Instructions](#general-instructions)
    -   [Exercise 1: Clouds and
        Infrared.](#exercise-1-clouds-and-infrared.)
    -   [Exercise 2: Water Vapor
        Feedback](#exercise-2-water-vapor-feedback)

# Exercises with clouds and feedbacks

# Exercises

These are the exercises you will work for the lab this week.

## General Instructions

For this week’s lab, when you write up the answers, I would like you to
think about integrating your R code chunks with your text.

For instance, you can describe what you’re going to do to answer the
question, and then for each step, after you describe what you’re going
to do in that step, you can include an R code chunk to do what you just
described, and then the subsequent text can either discuss the results
of what you just did or describe what the next step of the analysis will
do.

This way, your answer can have several small chunks of R code that build
on each other and follow the flow of your text.

## Exercise 1: Clouds and Infrared.

**Note:** this exercise only considers the effect of clouds on longwave
radiation and ignores the effect of clouds on albedo, which is also
important.

1.  Run the MODTRAN model with the default conditions: present-day
    CO<sub>2</sub> (400 ppm), a tropical atmosphere, and the sensor
    looking down from an altitude of 70 km. Plot the outgoing infrared
    spectrum.

    Run MODTRAN four times: first with no clouds, and then with three
    different kinds of clouds: standard cirrus, altostratus, and stratus
    (`clouds = "standard cirrus"`, `clouds = "altostratus"`, and
    `clouds = "stratus"`). These correspond to clouds at high, medium,
    and low altitude, respectively.

    Describe the important differences between the spectra for the four
    cases. Describe the differences in the intensity of outgoing
    infrared radiation *I*<sub>out</sub> for the four cases.

    How do the four spectra compare for the band of wavenumbers from
    about 600–750 cm<sup>-1</sup> (where CO<sub>2</sub> absorbs
    strongly) and the band from about 800–1200 cm<sup>-1</sup> (the
    atmospheric window)?

    Which kind of cloud has the greatest impact on outgoing infrared
    light? Why?

2.  Keeping the default settings (sensor altitude = 70 km looking down),
    Set `atmosphere = "midlatitude winter"` and `h2o_scale=1` and run
    MODTRAN with no clouds.

    Next, run MODTRAN with the same settings, but with `altitude_km = 0`
    and `looking="up"`. This means your sensor is on the ground looking
    up at the longwave radiation coming down from the atmosphere to the
    ground instead of looking down from the top of the atmosphere at the
    longwave radiation going out to space.

    Plot the two spectra (looking down from 70 km and looking up from
    the ground) and describe what you see. Pay special attention to the
    parts of the spectrum corresponding to the strong CO<sub>2</sub>
    absorption (roughly 600–750 cm<sup>-1</sup>) and the infrared window
    (roughly 800–1200 cm<sup>-1</sup>).

    Which parts of the spectrum correspond to warmer temperatures
    temperatures when you look down, and which parts correspond to
    colder temperatures? What about when you are looking up from the
    ground? Do you notice a pattern?

3.  Now, run MODTRAN with the sensor looking up from the ground
    (`altitude = 0` and `looking = "up"`), but with stratus clouds
    (`clouds = "stratus"`).

    When we’re looking up at the clouds, the base (bottom) of the clouds
    form a layer that is opaque to longwave radiation, with an
    emissivity of 1 (i.e., a perfect black body).

    Make a note of *I*<sub>down</sub> for the clear sky and with clouds.
    (Remember that the variable `i_out` in the MODTRAN output measures
    the intensity of longwave radiation reaching the sensor. In this
    exercise, the sensor is on the ground looking up, so `i_out`
    measures the downward radiation reaching the ground.)

    Plot the spectra for both cases and also compare *I*<sub>down</sub>.

    -   What part of the spectrum is most affected by clouds? (Answer
        both in terms of what ranges of wavelengths or wavenumbers are
        affected, and also what name we give to this part of the
        spectrum).
    -   On a winter night in Nashville, would it be colder if the sky is
        clear or if it’s cloudy?

4.  Now set `clouds` to `"none"`, and keep the sensor altitude at 0 km
    (`altitude_km = 0`) looking up (`looking = "up"`).

    Run MODTRAN first with `h2o_scale = 1` (the default), and then with
    `h2o_scale = 0` (no water vapor).

    Plot the two spectra (with water vapor and without water vapor) and
    compare them. Discuss why you see what you see:

    -   For the atmosphere with no water vapor, compare the parts of the
        spectrum corresponding to the strong CO<sub>2</sub> absorption
        (roughly 600–750 cm<sup>-1</sup>) and the infrared window
        (roughly 800–1200 cm<sup>-1</sup>).

        -   Which parts of the spectrum correspond to higher emission
            temperatures and which to lower temperatures?
        -   Why do you think this is?

    -   For the atmosphere with normal water vapor (`h2o_scale = 1`),
        how does water vapor change the spectrum you see from the
        ground?

        -   Does it make the longwave radiation brighter (warmer) or
            dimmer (cooler)?
            -   Why do you think this is?

## Exercise 2: Water Vapor Feedback

For this exercise, you will use the RRTM model to examine climate
sensitivity and the water vapor feedback in a radiative-convective
atmosphere.

1.  First, run the RRTM model with its default parameters (400 ppm
    CO<sub>2</sub>) and note the surface temperature (`T_surface`).

    Then run it again with doubled CO<sub>2</sub> concentration
    (`co2 = 800`). Adjust the surface temperature to bring the heat
    imbalance `Q` to zero (it may be easier to do this with the
    interactive model at <http://climatemodels.uchicago.edu/rrtm/> and
    then paste the new surface temperature into your R code).

    The change in surface temperature between the 400 ppm CO<sub>2</sub>
    and 800 ppm CO<sub>2</sub> (*Δ**T*<sub>2 × CO<sub>2</sub></sub>)
    runs is the **climate sensitivity**. What is it?

2.  Now run the RRTM model again, with 400 ppm CO<sub>2</sub>, but this
    time setting `relative_humidity = 0` (this turns off the water vapor
    feedback). Adjust `T_surface` to bring the heat into balance (so the
    output has `Q` equal to zero). Note the value of `T_surface`.

    Now double the CO<sub>2</sub> concentration (to 800 ppm) and adjust
    `T_surface` to bring the heat into balance. What is the climate
    sensitivity *Δ**T*<sub>2 × CO<sub>2</sub></sub> when there is no
    water-vapor feedback?

3.  Compare the climate sensitivity
    (*Δ**T*<sub>2 × CO<sub>2</sub></sub>) in part (a) (with water-vapor
    feedback) and part (b) (without water-vapor feedback). The
    amplification factor for the water-vapor feedback is the ratio of
    the climate sensitivity with water-vapor feedback to the sensitivity
    without the feedback. What is the amplification factor?

In your write-up, discuss how including the water vapor feedback changes
the way that CO<sub>2</sub> affects the climate.

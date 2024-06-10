## About me

```java
import com.google.common.collect.ImmutableMap;
import lombok.extern.slf4j.Slf4j;

import java.util.List;
import java.util.Map;

@Slf4j
public class AboutMe {

    public record Mat(Attributes attributes) {

        Mat() {
            this(new Attributes());
        }

        public List<String> getHobbies() {
            return attributes.hobbies();
        }

        public Map<String, Object> getLife() {
            return attributes.life();
        }

        public Map<String, Object> getCoding() {
            return attributes.coding();
        }

        public void displayInfo() {
            log.info("Hobbies: {}", String.join(", ", getHobbies()));
            log.info("Life: {}", getLife());
            log.info("Coding: {}", getCoding());
        }
    }

    public record Attributes(
            List<String> hobbies,
            Map<String, Object> life,
            Map<String, Object> coding) {

        public Attributes() {
            this(
                    List.of(
                            "🎹 Playing the piano",
                            "🎧 Listening to music",
                            "💻 Coding",
                            "🎬 Watching movies",
                            "📺 Watching TV series",
                            "🏋️‍♂️ Working out",
                            "🥾 Hiking",
                            "🏃 Running",
                            "🏀 Playing basketball",
                            "✈️ Traveling"
                    ),
                    ImmutableMap.of(
                            "Languages", List.of("🇮🇹 Italian", "🇬🇧 English"),
                            "Age", 30 + (int) (Math.random() * 6)
                    ),
                    ImmutableMap.of(
                            "Languages", ImmutableMap.of(
                                    "Expert", List.of("Java"),
                                    "Intermediate", List.of("JavaScript", "TypeScript", "Vue.js"),
                                    "Learning", List.of("Node.js", "Python")),
                            "Specialities", List.of(
                                    "🖥 Back end",
                                    "📚 Full stack",
                                    "🐳 Docker Compose stacks",
                                    "📱 Hybrid web apps"
                            ),
                            "IDEs", List.of("💡 IntelliJ IDEA", "📘 VS Codium"),
                            "PCs", ImmutableMap.of(
                                    "Linux", ImmutableMap.of(
                                            "Processor", "🖥 AMD Ryzen 5",
                                            "RAM", "🧠 64 GB",
                                            "GPU", "🎮 NVIDIA GeForce RTX 4060 Ti"),
                                    "Trashed (Windows)", ImmutableMap.of(
                                            "Processor", "🖥 Intel i7",
                                            "RAM", "🧠 16 GB",
                                            "GPU", "🎮 MSI R6870 Hawk")
                            )
                    )
            );
        }
    }

    public static void main(final String[] args) {
        final Mat mat = new Mat();
        mat.displayInfo();
    }
}
```

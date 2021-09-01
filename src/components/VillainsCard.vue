<template>
  <div class="villain-card" :style="image">
    <div className="villain-card-content">
      <h2 className="villain-card-name">
        {{name ? name : 'Villain'}}
      </h2>
      <p className="villain-card-description">
        {{description}}
      </p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'VillainsCard',
  props: ['url', 'name', 'description'],
   data() {
    return {
      image: { backgroundImage: `url(${this.url})`  }
    };
  }
}
</script>

<style scoped>


.villain-card {
  position: relative;
  display: flex;
  align-items: flex-end;
  overflow: hidden;
  padding: 1rem;
  text-align: center;
  color: whitesmoke;
  background-size: cover;
  background-color: whitesmoke;
  background-position: center;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1), 0 2px 2px rgba(0, 0, 0, 0.1), 0 4px 4px rgba(0, 0, 0, 0.1), 0 8px 8px rgba(0, 0, 0, 0.1), 0 16px 16px rgba(0, 0, 0, 0.1);
}
@media (min-width: 600px) {
  .villain-card {
    height: 540px;
 }
}


.villain-card-content {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  padding: 1rem;
  transition: transform var(--delay) var(--cubic);
  z-index: 1;
  color: #fff;
}

.villain-card-content > * + * {
  margin-top: 1rem;
}

.villain-card-name {
  font-size: 1.4rem;
  font-weight: bold;
  line-height: 1.2;
  color: #fff;
  background-color: rgba(0, 0, 0, 0.7);
  border-radius: 10px;
  padding: 2px 8px;
}

.villain-card-description {
  font-size: 1rem;
  font-style: italic;
  line-height: 0.9rem;
  white-space: pre-wrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 250px;
  max-height: 130px;
  opacity: 0;
}


</style>
